# BUN Files
These are the vast majority of assets resides

## File Structure

BUN Files are disposed as a tree (we call these blocks/chunks):

The first 4 bytes are the **type** of the chunk, the next 4 are the **length** in bytes of the chunk

## Non-Leaf Nodes
The first byte of the type also determines the type inside the tree: if the byte contains 0x80 ((id & 0x80000000) == 0x80000000), then the block is a non-leaf one,
it contains just other children, that can be parsed recursively as above
If the first byte is NOT 0x80, then we can safely say it's a leaf node of the tree

## Types

The canonical list can be found in NFSTools AssetDumper: https://github.com/NFSTools/NFS-ModTools/blob/master/ChunkView/Resources/ChunkDef.txt

The table below contains the elements I analysed, if it's not here then it means I still don't know the usage
For Each Hex, we define the Name used by ChunkViewer, and the name used by Binary

| Hex | Name (ChunkView) | Name (Binary) | Description | Link |
|-----|------------------|---------------|-------------|------|
| 0x00000000 | _N/A_ | Padding | Padding for the file, probably for alignment | _N/A_
| 0xB3300000 | BCHUNK_SPEED_TEXTURE_PACK_LIST_CHUNKS | TPKBlocks | Texture Container | [Texture](../textures/TextureBlock.md)
| 0xB3310000 | _N/A_ | TPK_InfoBlock | Container of multiple Texture Metadata/Header  | [TextureInfo](../textures/TextureInfoBlock.md)
| 0xB3320000 | _N/A_ | TPK_DataBlock | Contiainer of Texture Data | [TextureDataBlock](../textures/TextureDataBlock.md)
| 0x33310001 | _N/A_ | TPK_InfoPart1 | Texture Info Part1 | [TextureInfoPart1](../textures/TextureInfoPart1.md)
| 0x33310002 | _N/A_ | TPK_InfoPart2 | Texture Info Part2 | [TextureInfoPart2](../textures/TextureInfoPart2.md)
| 0x33310003 | _N/A_ | TPK_InfoPart3 | Texture Info Part3 | [TextureInfoPart3](../textures/TextureInfoPart3.md)
| 0x33310004 | _N/A_ | TPK_InfoPart4 | Texture Info Part4 | [TextureInfoPart4](../textures/TextureInfoPart4.md)
| 0x33310005 | _N/A_ | TPK_InfoPart5 | Texture Info Part5 | [TextureInfoPart5](../textures/TextureInfoPart5.md)