# TextureBlock

## Type Byte
**Hex:** 0xB3310000
**ChunkView**: N/A
**Binary:** TPK_InfoBlock

## Length
Dictionary: the length is the sum of the children inside

## Topology
Container Node - It Contains:
- One instance of [TextureInfoPart1](./TextureInfoPart1.md)
- One instance of [TextureInfoPart2](./TextureInfoPart2.md)
- One of these two: 
    - One instance of [TextureInfoPart3](./TextureInfoPart3.md)
    - One instance of [TextureInfoPart4](./TextureInfoPart4.md)
- One instance of [TextureInfoPart5](./TextureInfoPart5.md)


## Description
Container of Texture Headers