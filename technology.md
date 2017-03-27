# Technology used

## Defold

## Tiled Map Editor

As of April 2017 Defold does not include native support for non-orthogonal tilemaps. Fortunately, there is a number of platform-agnostic map editors available including Tiled, an open-source offering in active development since 2008. It is by far the most popular choice with 2D game creators. I have chosen this software because it enables creation of isometric tilemaps, a deliberate design choice for my game.

![Screenshot of Tiled Map Editor](images/tiled.png)

The output file includes tile definitions (pairings of image file and its size with a unique tile id) which are grouped in tilesets, each containing information about offsets and the draw sizes of tiles contained within.

The second part of the output structure includes layer definitions. Each layer has a size, offset from origin and a serialized array which contains placed tiles.

Please keep in mind that the aforementioned contents are in no way an exhaustive listing of data included in the output file.
