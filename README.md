# Shopify - Tailwing - AlpineJS

## Commands

### Laravel mix
Installing laravel-mix to compile JS / SCSS while creating ```webpack.mix.js``` file

``` Laravel installation
$ npm init -y
$ npm install laravel-mix --save-dev
$ touch webpack.mix.js
```
We add configuration to the ```webpack.mix.js```
 - https://laravel-mix.com/docs/6.0/examples
```
// webpack.mix.js
let mix = require('laravel-mix');

mix.js('src/js/app.js', 'assets')
   .sass('src/scss/app.scss', 'assets');
```
Running laravel mix

```
$ npx mix
```
Or while coding create a watch command w/
```
$ npx mix watch
```

### Tailwind
Installing Tailwind while creating ```tailwind.config.js``` file

``` Tailwind installation
$ npm install -D tailwindcss
$ npx tailwindcss init
```

We add the configuration to ```tailwind.config.js``` reviewing all files that might get tailwind classes.
- https://tailwindcss.com/docs/installation

```
  content: [
    './config/*.json',
    './layout/*.liquid',
    './assets/*.liquid',
    './sections/*.liquid',
    './snippets/*.liquid',
    './templates/*.liquid',
    './templates/*.json',
    './templates/customers/*.liquid'
  ],
```

Adding the tailwind imports to the ```src/scss/app.scss```
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Before deploying we can minify the css
```
$ npx tailwindcss -o assets/app.css --minify
```

### Alpine JS

```
$ npm install alpinejs
```
Adding the Alpine imports to the ```src/js/app.js```
```
import Alpine from 'alpinejs'
window.Alpine = Alpine
Alpine.start()
```

### Shopify
Pull the latest dawn theme form your store

Add the files the next lines of code into ```layout/theme.liquid``` just above ```</head>```

```
{% comment %} App CSS Configs {% endcomment %}
{{ 'app.css' | asset_url | stylesheet_tag }}
<script src="{{ 'app.js' | asset_url }}" async></script>
```