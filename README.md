# Vite-Svelte-TS-Bulma-Bulmaswatch-ionicons

This template should help get you started developing with Svelte and TypeScript in Vite.

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## Installation from scratch

### Insalling Vite

[Vite](https://vitejs.dev/)

```
C:\ npm init vite@latest
? Project name: ... vite-project
? Select a framework: » Svelte
? Select a variant: » TypeScript
C:\ cd vite-project
```

### Installing bulma and node-sass

[Bulma with Sass](https://bulma.io/documentation/customize/with-node-sass/)

```
npm install node-sass --save-dev
npm install bulma --save-dev
C:\ cat .\package.json
{
  "name": "vite-project",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "check": "svelte-check --tsconfig ./tsconfig.json"
  },
  "devDependencies": {
    "@sveltejs/vite-plugin-svelte": "^2.0.0",
    "@tsconfig/svelte": "^3.0.0",
    "bulma": "^0.9.4",
    "node-sass": "^8.0.0",
    "svelte": "^3.54.0",
    "svelte-check": "^2.10.0",
    "tslib": "^2.4.1",
    "typescript": "^4.9.3",
    "vite": "^4.0.0"
  }
```

### Include Bulma in build

[Bulma](https://bulma.io/)

```
C:\ mkdir sass
C:\ '@charset "utf-8";','@import "../node_modules/bulma/bulma.sass";' | Out-File sass\styles.scss
```

### New commands to package.json

Add to package.json:

```
"scripts": {
  "css-build": "node-sass --omit-source-map-url sass/styles.scss css/styles.css",
  "css-watch": "npm run css-build -- --watch",
  "start": "npm run css-watch"
}
```

This should now work:

```
C:\ npm run css-build

> vite-project@0.0.0 css-build
> node-sass --omit-source-map-url sass/styles.scss css/styles.css

Rendering Complete, saving .css file...
Wrote CSS to C:\vite-project\css\styles.css
```

### Bulmaswatch for a quick template

[ionicons](https://jenil.github.io/bulmaswatch/)

```
npm install bulmaswatch
```

Update vite-project\css\styles.scss (change flatly to any other template):

```
@import "../node_modules/bulmaswatch/flatly/variables";
<any changes to default variables here>
@import "../node_modules/bulma/bulma.sass";
@import "../node_modules/bulmaswatch/flatly/overwrite";
<any local (to this app) here if we want to override the overridden
```

### ionicons

[ionicons](https://ionic.io/ionicons)

Add to bottom of vite-project\index.html:

```
<script type="module" src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.esm.js"></script>
<script nomodule src="https://unpkg.com/ionicons@5.5.2/dist/ionicons/ionicons.js"></script>
```

## Technical considerations

**Why use this over SvelteKit?**

- It brings its own routing solution which might not be preferable for some users.
- It is first and foremost a framework that just happens to use Vite under the hood, not a Vite app.

This template contains as little as possible to get started with Vite + TypeScript + Svelte, while taking into account the developer experience with regards to HMR and intellisense. It demonstrates capabilities on par with the other `create-vite` templates and is a good starting point for beginners dipping their toes into a Vite + Svelte project.

Should you later need the extended capabilities and extensibility provided by SvelteKit, the template has been structured similarly to SvelteKit so that it is easy to migrate.

**Why `global.d.ts` instead of `compilerOptions.types` inside `jsconfig.json` or `tsconfig.json`?**

Setting `compilerOptions.types` shuts out all other types not explicitly listed in the configuration. Using triple-slash references keeps the default TypeScript setting of accepting type information from the entire workspace, while also adding `svelte` and `vite/client` type information.

**Why include `.vscode/extensions.json`?**

Other templates indirectly recommend extensions via the README, but this file allows VS Code to prompt the user to install the recommended extension upon opening the project.

**Why enable `allowJs` in the TS template?**

While `allowJs: false` would indeed prevent the use of `.js` files in the project, it does not prevent the use of JavaScript syntax in `.svelte` files. In addition, it would force `checkJs: false`, bringing the worst of both worlds: not being able to guarantee the entire codebase is TypeScript, and also having worse typechecking for the existing JavaScript. In addition, there are valid use cases in which a mixed codebase may be relevant.

**Why is HMR not preserving my local component state?**

HMR state preservation comes with a number of gotchas! It has been disabled by default in both `svelte-hmr` and `@sveltejs/vite-plugin-svelte` due to its often surprising behavior. You can read the details [here](https://github.com/rixo/svelte-hmr#svelte-hmr).

If you have state that's important to retain within a component, consider creating an external store which would not be replaced by HMR.

```ts
// store.ts
// An extremely simple external store
import { writable } from "svelte/store";
export default writable(0);
```
