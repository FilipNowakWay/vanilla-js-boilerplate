# Vanilla JS Boilerplate

Minimal Webpack 5 starter for plain JavaScript projects. No frameworks — just a dev server, a production build, ESLint, Prettier, and a clean `src/` to grow into.

## Quick start

```bash
npm install
npm run dev
```

The dev server runs at <http://localhost:8080>.

## Scripts

| Command                | Description                                       |
| ---------------------- | ------------------------------------------------- |
| `npm run dev`          | Start the dev server with inline source maps      |
| `npm run build`        | Build minified files into `dist/`                 |
| `npm run deploy`       | Format, build and publish `dist/` to GitHub Pages |
| `npm run lint`         | Check files with ESLint                           |
| `npm run lint:fix`     | Fix auto-fixable ESLint errors                    |
| `npm run format`       | Format files with Prettier                        |
| `npm run format:check` | Check formatting without changing files           |

`npm run deploy` runs format first, so the published `dist/` is always built from formatted source. Lint is not part of the deploy pipeline — run it separately if needed.

## Linting and formatting

ESLint checks JavaScript, JSON, Markdown, CSS, and shell files using the flat config in `eslint.config.js`. Generated files (`dist/`, `package-lock.json`) are skipped.

Prettier formats the project. Paths listed in `.prettierignore` (`node_modules/`, `dist/`, `package-lock.json`) are left untouched.

Run both checks before committing:

```bash
npm run lint
npm run format:check
```

Use `npm run lint:fix` and `npm run format` to apply fixes automatically.

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
