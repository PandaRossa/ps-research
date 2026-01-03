# TextureBlock

## Type Byte
**Hex:** 0xB3300000
**ChunkView**: BCHUNK_SPEED_TEXTURE_PACK_LIST_CHUNKS
**Binary:** TPKBlocks

## Length
Dictionary: the length is the sum of the children inside

## Topology
Container Node: It contains two types of children, 
- one instance of [TextureInfoBlock](./TextureInfoBlock.md) 
- one instance of [TextureDataBlock](./TextureDataBlock.md)

## Description
Texture Container, the TextureInfoBlock contains the metadata, the TextureDataBlock the content