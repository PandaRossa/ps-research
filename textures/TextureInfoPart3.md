# TextureInfoPart3

## Type Byte
**Hex:** 0x33310003
**ChunkView**: N/A
**Binary:** TPK_InfoPart3

## Length
Dynamic - Multiple 24 bytes structs

## Topology
Leaf Node of [TextureInfoBlock](./TextureInfoBlock.md)

## Description
Texture Metadata for Compressed Texture Blocks

## Structure

For each 24 bytes: 

| Length | Type | Name | Description|
|----------|------|------|------------|
| 4 | u32 | Key | Key | |
| 4 | s32 | AbsoluteOffset |  Offset where to start to decompress relative to the TextureInfoPart2 Content |
| 4 | s32 | EncodedSize | Size of the block before Decompressing 
| 4 | s32 | DecodedSize | Size of the block after Decompressing 
| 1 | byte | UserFlags | 
| 1 | byte | Flags | Determines how to decompress the file, at the moment I only found "2" as a value
| 2 | s16 | RefCount |
| 4 | s32 | Unknown