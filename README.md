<h1>Sasses</h1>

<img src="logo.png" align="right" alt="Size Limit logo by Anton Lovchikov" width="150">

<p>
    <img src="https://img.shields.io/npm/v/sasses" />&nbsp;<img src="https://img.shields.io/npm/dm/sasses" />&nbsp;<img src="https://img.shields.io/npm/l/sasses" />
</p>

<p>Sass modules provide more advanced functions.</p>
<p>
    <ul>
        <li><b><a href="md/api/color.md">sasses/color</a>:</b> Generates new colors based on existing ones, making it easy to build color themes.</li>
        <li><b><a href="md/api/list.md">sasses/list</a>:</b> Lets you access and modify values in lists.</li>
        <li><b><a href="md/api/map.md">sasses/map</a>:</b> Makes it possible to look up the value associated with a key in advanced map.</li>
        <li><b><a href="md/api/math.md">sasses/math</a>:</b> Provides functions that operate on advanced numbers.</li>
        <li><b><a href="md/api/meta.md">sasses/meta</a>:</b> Exposes the advanced details of Sass’s inner workings.</li>
        <li><b><a href="md/api/selector.md">sasses/selector</a>:</b> Provides access to Sass’s powerful selector engine.</li>
        <li><b><a href="md/api/string.md">sasses/string</a>:</b> Provides more advanced string functions for Sass.</li>
    </ul>
</p>

<h2>Requires</h2>
<ul>
    <li>Dart Sass: <code>>=1.33.0</code></li>
</ul>

<h2>Install</h2>
<p>NPM Package:</p>

```bash
npm install sasses
```

<h2>How To Use</h2>
<p>Use the package like any other Sass module:</p>

```sass
// General
@use 'sasses'

// Specific
@use 'sasses/color'
@use 'sasses/list'
@use 'sasses/map'
@use 'sasses/math'
@use 'sasses/meta'
@use 'sasses/selector'
@use 'sasses/string'
```

<p>Depending on your setup, you may need to configure <code>node_modules</code> as include path:</p>

```javascript
const sass = require("sass");

sass.render({
  file: scss_filename,
  includePaths: ["node_modules"],
});
```
