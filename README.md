# Vue 3 + TypeScript + Vite + Less + ESLint + Prettier + husky + lint-staged + Stylelint + commitlint

## Vue 3 + Typescript + Vite

- PowerShell

```PowerShell
npm create @vitejs/app vue-vite
```

## Less

- PowerShell

```PowerShell
npm i -D Less
```

- App.vue

```Vue
import './assets/styles/app.less';
```

## ESLint

- PowerShell

```PowerShell
npm i -D eslint
```

- .eslintrc.json

```JSON
"rules": {
 "indent": [
  "error",
  2,
  {
   "SwitchCase": 1
  }
 ],
 "linebreak-style": [
  "error",
  "unix"
 ],
 "no-console": [
  "warn",
  {
   "allow": [
    "warn",
    "error"
   ]
  }
 ],
 "quotes": [
  "error",
  "single"
 ],
 "semi": [
  "error",
  "always"
 ]
}
```

## CSpell

- PowerShell

```PowerShell
npm i -D cspell
```

- .vscode\settings.json

```JSON
{
  "cSpell.words": [
    "Avenir",
    "esnext",
    "linebreak",
    "singlefile",
    "vite",
    "vitejs"
  ]
}
```

## SFC: Single File Component

- PowerShell

```PowerShell
npm i -D vite-plugin-singlefile
```

- vite.config.ts

```TypeScript
import { defineConfig } from "vite"
import vue from "@vitejs/plugin-vue"
import { viteSingleFile } from "vite-plugin-singlefile"

export default defineConfig({
 plugins: [vue(), viteSingleFile()],
 build: {
  target: "esnext",
  assetsInlineLimit: 100000000,
  chunkSizeWarningLimit: 100000000,
  cssCodeSplit: false,
  brotliSize: false,
  rollupOptions: {
   inlineDynamicImports: true,
   output: {
    manualChunks: () => "everything.js",
   },
  },
 },
})
```

## Removing hash codes from vite packaged files

- vite.config.ts

```TypeScript
rollupOptions: {
 output: {
  entryFileNames: `assets/[name].js`,
  chunkFileNames: `assets/[name].js`,
  assetFileNames: `assets/[name].[ext]`,
 }
}
```

## Set file location of .eslintcache

- package.json

```JSON
"scripts": {
    "eslint": "eslint --cache --cache-location \"node_modules\\.cache\\.eslintcache\" --max-warnings 0 \"{src,mock}/**/*.{vue,ts,tsx,js,jsx}\" --fix",
  },
```

## Solve Network: use \`--host` to expose

- vite.config.ts

```TypeScript
export default defineConfig({
 server: {
  host: '0.0.0.0'
 }
})
```

## Read JSON

- public/app.json

```JSON
{
  "msg": "Hello Vue 3 + TypeScript + Vite + Less + ESLint + SFC"
}
```

- src/App.vue

```Vue
<script setup lang="ts">
import json from '../public/app.json';
</script>

<template>
  <HelloWorld :msg="json.msg" />
</template>
```
