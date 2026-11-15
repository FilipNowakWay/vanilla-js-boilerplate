# Vanilla JS Boilerplate

Minimal Webpack 5 starter for plain JavaScript projects. No frameworks, no opinions — just a dev server, a production build, and a clean `src/` to grow into.

## Quick start

```bash
npm install
npm run dev
```

The dev server runs at <http://localhost:8080>.

## Scripts

| Command         | Description                                          |
| --------------- | ---------------------------------------------------- |
| `npm run dev`   | Start the dev server with inline source maps         |
| `npm run build` | Build minified files into `dist/`                    |
| `npm run deploy`| Build and publish `dist/` to GitHub Pages         |

## Project structure

```text
src/
├── assets/        images, fonts, and other static files
├── components/    reusable UI components
├── modules/       JavaScript modules
├── styles/        CSS files
├── index.js       application entry point
└── template.html  HTML template used by HtmlWebpackPlugin
```

Styles and assets imported from JavaScript are bundled automatically:

```js
import "./styles/main.css";
```

## Removing `.gitkeep` files

The empty folders ship with `.gitkeep` files so git tracks them. Once the folders contain real files, delete the placeholders:

```bash
find src -name ".gitkeep" -type f -delete
```

## Optional: html-loader

Ask yourself: **does `template.html` reference files directly?**

- A CSS file via `<link rel="stylesheet" href="./styles/main.css">`?
- An image via `<img src="./assets/images/photo.png">`?

If **yes**, install html-loader so Webpack resolves and bundles those references:

```bash
npm install --save-dev html-loader
```

Then add it to `webpack.config.js`:

```js
module: {
  rules: [
    {
      test: /\.html$/i,
      loader: "html-loader",
    },
  ],
}
```

If **no** — keep importing CSS and assets from JavaScript, and you don't need html-loader.

## Requirements

Node.js 22.15 or newer.

## License

MIT — see [LICENSE](./LICENSE).
