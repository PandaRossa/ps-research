# TextureInfoPart4

## Type Byte
**Hex:** 0x33310004  
**ChunkView**: N/A  
**Binary:** TPK_InfoPart4

## Length
Dynamic – array of texture records.  
Each record has a fixed 89‑byte header (88 bytes of fields + 1 byte name length) followed by a variable‑length ASCII name string.

## Topology
Leaf Node of [TextureInfoBlock](./TextureInfoBlock.md)

## Structure

For each texture entry:

| Size | Type    | Name             | Description |
|------|---------|------------------|-------------|
| 4    | u32  | `CubeEnvironment`   |
| 8    | u8s   | `Unknown`          | Unknown 8‑byte field (copied from the binary, purpose not yet confirmed). |
| 4    | u32   | `BinKey`         | Hash of the textures (used by the models) |
| 4    | u32  | `ClassKey`       |  |
| 4    | s32   | `Offset`         | Offset (in bytes) to the texture pixel data within the TPK data section. |
| 4    | s32   | `PaletteOffset`  | Offset (in bytes) to the palette data within the TPK data section, or `-1` if no palette. |
| 4    | u32  | `OtherSize`      | Size (in bytes) of the main texture data block. |
| 4    | u32  | `PaletteSize`    | Size (in bytes) of the palette data block. |
| 4    | u32  | `Area`           | |
| 2    | u16  | `Width`          | Texture width in pixels. |
| 2    | u16  | `Height`         | Texture height in pixels. |
| 2    | u16  | `Logs`           | |
| 1    | u8    | `CompressionType` | Compression / pixel‑format type, see `TextureCompressionType` enum |
| 1    | u8    | `PalComp`        |  |
| 2    | s16   | `NumPalettes`    |  |
| 1    | u8    | `Mipmaps`        |  |
| 1    | u8    | `TilableUV`      | UV tiling behavior, see `TextureTilableType` enum. |
| 1    | u8    | `BiasLevel`      | |
| 1    | u8    | `RenderingOrder` | |
| 1    | u8    | `ScrollType`     | Texture scroll/animation mode, see `TextureScrollType` enum. |
| 1    | u8    | `Used`           | |
| 1    | u8    | `ApplyAlphaSort` | |
| 1    | u8    | `Usage`          | Alpha usage type, see `TextureAlphaUsageType` enum. |
| 1    | s8   | `AlphaBlendType`  | Alpha blending mode, see `TextureAlphaBlendType` enum. |
| 1    | u8    | `Flags`          | Miscellaneous per‑texture flags (bitfield, not fully documented). |
| 1    | u8    | `MipmapBiasType` | Mipmap bias profile, see `TextureMipmapBiasType` enum. |
| 1    | u8    | `Padding`        | Padding / alignment byte (usually zero). |
| 2    | s16   | `ScrollTimestep` | Time step used for texture scrolling/animation. |
| 2    | s16   | `ScrollSpeedS`   | Scroll speed along the S (U) texture coordinate. |
| 2    | s16   | `ScrollSpeedT`   | Scroll speed along the T (V) texture coordinate. |
| 2    | s16   | `OffsetS`        | Base UV offset along S (U). |
| 2    | s16   | `OffsetT`        | Base UV offset along T (V). |
| 2    | s16   | `ScaleS`         | UV scale factor along S (U). |
| 2    | s16   | `ScaleT`         | UV scale factor along T (V). |
| 4    | u32  | `Unknown1`       | |
| 4    | u32  | `Unknown2`       | |
| 4    | u32  | `Unknown3`       | |
| 1    | u8    | `NameSize`       | |
| N    | char[]  | `Name`           | ASCII texture name (`NameSize` bytes), null terminated|

### Notes
Enum values below: 
```csharp
public enum TextureCompressionType : byte
{
    TEXCOMP_DEFAULT = 0,
    TEXCOMP_4BIT = 4,
    TEXCOMP_8BIT = 8,
    TEXCOMP_16BIT = 16,
    TEXCOMP_16BIT_1555 = 17,
    TEXCOMP_16BIT_565 = 18,
    TEXCOMP_16BIT_3555 = 19,
    TEXCOMP_24BIT = 24,
    TEXCOMP_32BIT = 32,
    TEXCOMP_DXT = 33,
    TEXCOMP_DXTC1 = 34,
    TEXCOMP_DXTC3 = 36,
    TEXCOMP_DXTC5 = 38,
    TEXCOMP_DXTN = 39,
    TEXCOMP_L8 = 40,
    TEXCOMP_DXTC1_AIR = 41,
    TEXCOMP_DXTC1_AIG = 42,
    TEXCOMP_DXTC1_AIB = 43,
    TEXCOMP_8BIT_16 = 128,
    TEXCOMP_8BIT_64 = 129,
    TEXCOMP_8BIT_IA8 = 130,
    TEXCOMP_4BIT_IA8 = 131,
    TEXCOMP_4BIT_RGB24_A8 = 140,
    TEXCOMP_8BIT_RGB24_A8 = 141,
    TEXCOMP_4BIT_RGB16_A8 = 142,
    TEXCOMP_8BIT_RGB16_A8 = 143,
}

public enum TextureTilableType : byte
{
    NONE = 0,
    HORIZONTAL = 1,
    VERTICAL = 2,
    ALL_SIDES = 3,
}

public enum TextureScrollType : byte
{
    TEXSCROLL_NONE = 0,
    TEXSCROLL_SMOOTH = 1,
    TEXSCROLL_SNAP = 2,
    TEXSCROLL_OFFSETSCALE = 3,
}

public enum TextureAlphaUsageType : byte
{
    TEXUSAGE_NONE = 0,
    TEXUSAGE_PUNCHTHRU = 1,
    TEXUSAGE_MODULATED = 2,
}

public enum TextureAlphaBlendType : sbyte
{
    TEXBLEND_DEFAULT = -1,
    TEXBLEND_SRCCOPY = 0,
    TEXBLEND_BLEND = 1,
    TEXBLEND_ADDATIVE = 2,
    TEXBLEND_SUBTRACTIVE = 3,
    TEXBLEND_OVERBRIGHT = 4,
    TEXBLEND_DEST_BLEND = 5,
    TEXBLEND_DEST_ADDATIVE = 6,
    TEXBLEND_DEST_SUBTRACTIVE = 7,
    TEXBLEND_DEST_OVERBRIGHT = 8,
}

public enum TextureMipmapBiasType : byte
{
    TEXBIAS_DEFAULT = 0,
    TEXBIAS_ADS = 1,
    TEXBIAS_ARC = 2,
    TEXBIAS_OBJ = 3,
    TEXBIAS_ORG = 4,
    TEXBIAS_SGN = 5,
    TEXBIAS_TRN = 6,
    TEXBIAS_PARTICLES = 7,
    TEXBIAS_NUM = 8,
}
```
