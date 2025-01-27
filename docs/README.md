# Test tsc to emit mjs files
The goal is to setup typescript to emit `.mjs` files when the typescript file is set to `.ts`
This chapter: https://www.totaltypescript.com/books/total-typescript-essentials/configuring-typescript#how-does-typescript-know-what-module-system-to-emit
Includes the following table

| File Extension	| Emitted File Extension	| Emitted Module System            |
| ---             | ---                     | ---                              |
| album.mts       |	album.mjs	              | ESM                              |
| album.cts       |	album.cjs	              | CJS                              |
| album.ts	      | album.js 	              | Depends  on type in package.json |

> If we keep album.ts the same, TypeScript will look up the directories for the closest package.json file. If the type field is set to module, TypeScript will emit ESM syntax. If it's set to commonjs (or unset, matching Node's behavior), TypeScript will emit CJS syntax.

## Problem
The package.json specifies the module type: `"type": "module"`.  
So if I understand correctly, because the package.json has the type specified as module, and the tsconfig has `moduleDetection`, I expected that the build will emit `*.mjs`.

But it is emitting `*.js`

<img src='./Screenshot 2025-01-27 at 17.34.43.png' />

## Reproducing
To run the build, execute the following:
```sh
npm run build
```
