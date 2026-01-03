# TextureInfoPart1

## Type Byte
**Hex:** 0x33310001
**ChunkView**: N/A
**Binary:** TPK_InfoPart1

## Length
124 Bytes

## Topology
Leaf Node of [TextureInfoBlock](./TextureInfoBlock.md)

## Description
Name of the Texture Pack

## Structure

| Length | Type | Name | Description|
|----------|------|------|------------|
|  4 | u32 | Unknown | Unknown
| dynamic (aligned to 16 bytes) | null-terminated string | CollectionName | Name of the Texture Pack
| dynamic | null-terminated string | FileName | File of the texture pack (Don't know if it's used by the game)

## Noted 

None