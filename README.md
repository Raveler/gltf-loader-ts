# gltf-loader-ts [![status](https://img.shields.io/badge/glTF-2%2E0-green.svg?style=flat)](https://github.com/KhronosGroup/glTF)

[![npm Version](https://img.shields.io/npm/v/gltf-loader-ts.svg?style=flat)](https://www.npmjs.com/package/gltf-loader-ts)
[![Travis](https://img.shields.io/travis/bwasty/gltf-loader-ts/master.svg?style=flat&logo=travis)](https://travis-ci.org/bwasty/gltf-loader-ts)
[![Coveralls](https://img.shields.io/coveralls/github/bwasty/gltf-loader-ts.svg?style=flat)](https://coveralls.io/github/bwasty/gltf-loader-ts)
[![codecov](https://codecov.io/gh/bwasty/gltf-loader-ts/branch/master/graph/badge.svg)](https://codecov.io/gh/bwasty/gltf-loader-ts)
[![Tokei](https://tokei.rs/b1/github/bwasty/gltf-loader-ts)](https://github.com/Aaronepower/tokei)
[![Greenkeeper badge](https://badges.greenkeeper.io/bwasty/gltf-loader-ts.svg)](https://greenkeeper.io/)

Engine-agnostic glTF 2.0 loader in TypeScript.

_ALPHA VERSION - NOT ALL MAIN FEATURES IMPLEMENTED YET_

## Features
- can load glTF data from any source and provides unified access to binary and image data _[image loading not implemented yet]_:
    - source: URL (http) and `FileList` (e.g. drag-and-drop) _[drag-and-drop not implemented yet]_
    - plaintext .gltf with external buffer and image files (.bin and .png/.jpg)
    - plaintext with embedded buffer and image data (data URIs)
    - GLB
- JSON parts have types generated from the official JSON Schema (-> [`GlTf`](https://bwasty.github.io/gltf-loader-ts/interfaces/gltf.html))
- Lazy loading: external buffer and image files are only loaded when the data is accessed
  - option to pre-fetch everything
- Can report progress during loading via callbacks


## Installation
```
npm install --save-dev gltf-loader-ts
```
## Example
```typescript
import { GltfLoader } from 'gltf-loader-ts';
let loader = new GltfLoader();
let asset: Asset = await loader.load(
    'https://raw.githubusercontent.com/KhronosGroup/glTF-Sample-Models/master/2.0/Box/glTF/Box.gltf');
let gltf: GlTf = asset.gltf;
console.log(gltf);
// -> {asset: {…}, scene: 0, scenes: Array(1), nodes: Array(2), meshes: Array(1), …}

let data = await asset.bufferViewData(0); // fetches Box0.bin

// not implemented yet:
// let image: Image = await asset.imageData.get(0)
```

For a complete example, see [example/](example/).

Documentation: https://bwasty.github.io/gltf-loader-ts
