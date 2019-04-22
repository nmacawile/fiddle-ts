# Parcel setup

## Initializing the project directory

```sh
git init
npm init -y
```

## Installing Parcel

In addition to Parcel, also install `parcel-plugin-clean-dist` to clear the output directory  (`dist` by default) before every build. Parcel doesn't clear it on its own.

```sh
npm install parcel-bundler -D
npm install parcel-plugin-clean-dist -D
```

## Adding `dev` and `build` NPM scripts

The `dev` script launches a dev server that tracks changes in the `src` directory and compiles the files into the `dev` directory. You can add the `--open` option to launch the project with your default browser when the dev server is ready.

The `build` script compiles all the files in the `src` directory as minified files. Compiled files go into the `dist` directory (default).

`--no-source-map` option skips the creation source maps.

```json
//package.json
"scripts": {
  "dev": "parcel src/* --out-dir=dev --open",
  "build": "parcel build src/* --no-source-maps"
},
```

## Preparing the `src` directory

All source files should be placed in the `src` directory. There is no need to install `typescript` or `sass`. Parcel detects file formats and installs necessary dependencies dynamically.

Boilerplate code:

```
+ src/
+-- index.html
+-- scripts/
    +-- index.ts
+-- stylesheets/
    +-- styles.scss

```

```html
<!-- src/index.html -->
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>Fiddle</title>
    <link href="stylesheets/styles.scss" rel="stylesheet">
  </head>
  <body>
    <h1>Fiddle</h1>
    <p>
      Welcome!
    </p>
    <script src="scripts/index.ts"></script>
  </body>
</html>
```

```scss
/** stylesheets/styles.scss **/
html, body { height: 100%; }
body { 
  margin: 0;
  color: #fff;
  background-color: #000;
  padding: 1rem;
}
```

```typescript
// scripts/index.ts
console.log('Script is loaded.');
```

## Adding files to `.gitignore`

Don't forget to add these folders before pushing to remote repo.

```
# .gitignore
node_modules/
.cache/
dev/
dist/
```

## Launching the dev server

Use this command to run the dev server. Once your dev server is ready, you can go to `localhost:1234` to view your page.

```sh
npm run dev
```

## Production build

To compile your project, run:

```sh
npm run build
```

Compiled files are generated in the `dist` directory.

