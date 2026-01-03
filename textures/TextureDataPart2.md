# TextureInfoPart1

## Type Byte
**Hex:** 0x33320002
**ChunkView**: N/A
**Binary:** TPK_DataPart2

## Length
Variable

## Topology
Leaf Node of [TextureDataBlock](./TextureDataBlock.md)

## Description
Not yet discovered

## Structure

Parsing this is fairly complex, and it depends if it has a compressed [TextureInfoPart3](./TextureInfoPart3.md) or an uncompressed [TextureInfoPart4](./TextureInfoPart4.md)

Having the count of textures (from [TextureInfoPart2](./TextureInfoPart2.md)) is also needed

It's probably better to read how Binary itself gather and export the textures, since the complexity of this

### Uncompressed Texture
For each element in [TextureInfoPart4](./TextureInfoPart4.md):

- The content is at the offset: `Offset + 0x7C - 4`;
- The length of the content is in `OtherSize`
- Optionally Palette info can be found by using PaletteOffset (start at `PaletteOffset + 0x7C`) at length PaletteSize 

With the header info above and the content read you can reconstruct a DDS file for the texture

### Compressed Texture

Compressed Textures are more complex.

For each element in [TextureInfoPart3](./TextureInfoPart3.md)

- We check `Flags`, right now I only built the parser if `Flags` == 2

## Compressed - Flags 2
We start from `AbsoluteOffset` inside the block
We loop from Offset for `EncodedSize` bytes, tyring to find blocks starting with `0x55441122` (LZCOmpressed)
We then get this structure

| Size | Type | Name | Notes |
|------|------|------| ----- |
| 4 | s32 | DecodedSize | |
| 4 | s32 | EncodedSize | |
| 4 | s32 | DecodedDataPosition |  |
| 4 | s32 | EncodedDataPosition | |
| 8 | pdg | PaddingStart | |
| 1 | byte | Version | |
| 7 | pdg | Padding | |
| 4 | i32 | size | if version == 2, size must be incremented to 16 |

We get the Offset of PaddingStart, and we decompress to the length of size
Decompressing should return an array of size DecodedSize
We seek after `EncodedSize` and continue the loop

These blocks are then sorted by `DecodedDataPosition` and copied into a single array
The first 148 bytes of the last decompressed block contains the same header that has the same structure of [TextureInfoPart4](./TextureInfoPart4.md)

The rest of the data can be then used in the same way as Uncompressed Textures