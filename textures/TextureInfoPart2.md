# TextureInfoPart2

## Type Byte
**Hex:** 0x33310002
**ChunkView**: N/A
**Binary:** TPK_InfoPart2

## Length
8 Bytes * Number Of textures

## Topology
Leaf Node of [TextureInfoBlock](./TextureInfoBlock.md)

## Description
Probably Texture IDs - by dividing the length by 8 we get the number of textures inside the pack

## Structure

For each 8 bytes: 

| Length | Type | Name | Description|
|----------|------|------|------------|
|  8 | u64 | Unknown | Unknown

## Noted 

None