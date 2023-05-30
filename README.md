Typescript type definitions for the [.tmj](https://doc.mapeditor.org/en/stable/reference/json-map-format/#point) JSON tilemap structure exportable from the [Tiled](https://github.com/mapeditor/tiled) tilemap editor.

Should be useful for people developing js/ts apps that process output of the Tiled editor: for code completion, type validation, quick documentation view.

### Installation

Add this repo to `devDependencies` in your package.json:

```json
  "devDependencies": {
    "tiled-tmj-typedefs": "git+https://github.com/klesun/tiled-tmj-typedefs.git#1.10.1",
```

### Usage

```typescript
import type TiledMap from "tiled-tmj-typedefs/types/TiledMap";

const tilemap: TiledMap = await fetch("/assets/tilemap.tmj")
    .then(rs => rs.json());
for (const layer of tilemap.layers) {
    if (layer.type === "tilelayer") {
        for (let y = 0; y < layer.height; ++y) {
            for (let x = 0; x < layer.width; ++x) {
                const tileIndex = y * layer.width + x;
                const tilesetIndex = layer.data[tileIndex] - 1;
                const tileset = tilemap.tilesets[tilesetIndex];
                doSomethingWithTile(y, x, tileset.image);
            }
        }
    }
}
```

__________________

Feel free to submit PRs if you spot any inconsistencies. Typedefs were based on the documentation, but some optional fields may have been incorrectly specified as mandatory.

Packaged for the [Blockchain Cuties Universe](https://blockchaincuties.com/)
