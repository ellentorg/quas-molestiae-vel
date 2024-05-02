# @ellentorg/quas-molestiae-vel

This [vite](https://vitejs.dev/) plugin generates a single SVG spritemap containing multiple <symbol> elements from all `.svg` files in a directory.

<a href="https://www.npmjs.com/package/@ellentorg/quas-molestiae-vel">
  <img alt="npm version" src="https://img.shields.io/npm/v/@ellentorg/quas-molestiae-vel.svg?style=flat-square" />
</a>
<a href="https://www.npmjs.com/package/@ellentorg/quas-molestiae-vel">
  <img alt="npm downloads" src="https://img.shields.io/npm/dm/@ellentorg/quas-molestiae-vel.svg?style=flat-square" />
</a>

## Features

- Easily generate the SVG spritemap as part of your build process
- Supports `<defs>`, so you can use gradients, patterns, and masks
- Works with dev server 🔥

If you find this plugin useful, why not

<a href="https://www.buymeacoffee.com/gmakarov" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" width="160" height="40"></a>

## Installation

```bash
# using npm
npm install -D @ellentorg/quas-molestiae-vel
# using pnpm
pnpm install -D @ellentorg/quas-molestiae-vel
# using yarn
yarn add --dev @ellentorg/quas-molestiae-vel
```

## Usage

**Vite config**

```ts
import { svgSpritemap } from '@ellentorg/quas-molestiae-vel';

export default defineConfig({
  plugins: [
    svgSpritemap({
      pattern: 'src/icons/*.svg',
    }),
  ],
});
```

**SVG element**

```tsx
export const Icon: React.FC<{ name: string }> = ({ name }) => (
  <svg xmlns="http://www.w3.org/2000/svg" xmlnsXlink="http://www.w3.org/1999/xlink">
    <use xlinkHref={`/spritemap.svg#${name}`} />
  </svg>
);

const App = () => {
  return <Icon name="arrow" />;
};
```

## Options

| Option         | Type                                 | Description                                                                                   |
| -------------- | ------------------------------------ | --------------------------------------------------------------------------------------------- |
| `pattern`      | `string`                             | A glob pattern that specifies which SVG files to include in the sprite.                       |
| `prefix`       | `string` (optional)                  | A string that is added to the beginning of each SVG icon's ID when it is added to the sprite. |
| `filename`     | `string` (optional)                  | The name of the output file that contains the SVG sprite. Default is `spritemap.svg`.         |
| `currentColor` | `boolean` (optional)                 | Replace colors in the SVGs with the `currentColor` value by SVGO. Default is `true`.          |
| `svgo`         | `SVGOConfig` or `boolean` (optional) | Use SVGO for optimization. Default is `true`.                                                 |
