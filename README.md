<h1>Sasses</h1>

<img src="logo.png" align="right" alt="Size Limit logo by Anton Lovchikov" width="150">

<p>
    <a target="_blank" href="https://www.npmjs.com/package/sasses?activeTab=versions"><img src="https://img.shields.io/npm/v/sasses" /></a>&nbsp;<img src="https://img.shields.io/npm/dm/sasses" />&nbsp;<a target="_blank" href="https://github.com/officialxviid/sasses/blob/main/LICENSE"><img src="https://img.shields.io/npm/l/sasses" /></a>
</p>

<p>Sass modules provide more advanced functions.</p>
<p>
    <ul>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Break-Module">sasses/break</a>:</b> Provides mixins, functions, and variables for working with breakpoints and aids in responsive development in Sass.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Checker-Module">sasses/checker</a>:</b> Provides functions that operate on advanced checker.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Color-Module">sasses/color</a>:</b> Generates new colors based on existing ones, making it easy to build color themes.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Exception-Module">sasses/exception</a>:</b> Provides functions to standardize exception messages and assist with common validation for Sass.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/List-Module">sasses/list</a>:</b> Lets you access and modify values in lists.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Map-Module">sasses/map</a>:</b> Makes it possible to look up the value associated with a key in advanced map.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Math-Module">sasses/math</a>:</b> Provides functions that operate on advanced numbers.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Meta-Module">sasses/meta</a>:</b> Exposes the advanced details of Sass’s inner workings.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/Selector-Module">sasses/selector</a>:</b> Provides access to Sass’s powerful selector engine.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/String-Module">sasses/string</a>:</b> Provides more advanced string functions for Sass.</li>
        <li><b><a href="https://github.com/officialxviid/sasses/wiki/URL-Module">sasses/url</a>:</b> Provides more advanced a data URL.</li>
    </ul>
</p>

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
@use 'sasses/break'
@use 'sasses/checker'
@use 'sasses/color'
@use 'sasses/exception'
@use 'sasses/list'
@use 'sasses/map'
@use 'sasses/math'
@use 'sasses/meta'
@use 'sasses/selector'
@use 'sasses/string'
@use 'sasses/url'
```

<p>Depending on your setup, you may need to configure <code>node_modules</code> as include path:</p>

```javascript
const sass = require("sass");

sass.render({
  file: scss_filename,
  includePaths: ["node_modules"],
});
```

<h2>Docs</h2>
<p>Explore further on the <a target="_blank" href="https://github.com/officialxviid/sasses/wiki">wiki<sup>↗</sup></a> page that we have provided.</p>
