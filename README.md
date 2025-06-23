<p align="center">
    <img width="200" src="https://raw.githubusercontent.com/officialxviid/sasses/3c837cc01e97df4504b0ebd7796c548c1646245d/assets/images/logo/Sasses/SVG/SassesText%20-%20Solid.svg"/>
    <br><br>
    <strong>Sass modules (Sasses) provide more advanced variables, mixins and functions for Sass.</strong>
    <br><br>
    <a href="https://www.npmjs.com/package/sasses"><img alt="NPM Version" src="https://img.shields.io/npm/v/sasses"/></a>
    <a href="https://packagist.org/packages/officialxviid/sasses"><img alt="Composer Version" src="https://img.shields.io/packagist/v/officialxviid/sasses"/></a>
    <a href="https://github.com/officialxviid/sasses/blob/main/LICENSE.txt"><img alt="License" src="https://img.shields.io/github/license/officialxviid/sasses"/></a>
</p>

<h1>Getting Started</h1>

<h2>Require</h2>
<ul>
   <li>Dart Sass: <code>>= 1.23.0</code></li>
</ul>

<h2>Installation</h2>

<h3>
    <img height="20" src="https://www.svgrepo.com/show/355146/npm.svg"/>
    Node Package Manager (NPM)
</h3>

```bash
npm i sasses
```

<h3>
    <img height="20" src="https://packagist.org/img/logo-small.png?v=1748445971"/>
    Packagist
</h3>

```bash
composer require officialxviid/sasses
```

<h2>How to Use</h2>

<p>For example, we use the <code><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#parameter-type-function">parameter-type()</a></code> function in the <strong><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package">throw package</a></strong>.</p>

```scss
throw.parameter-type($context, $name, $value, $catch: false, $types...);
// or
parameter-type-exception($context, $name, $value, $catch: false, $types...);
```

<p>If you use a specific package, then:</p>

```scss
@use "sass:meta";
@use "sass:color";
@use "@sasses/throw";

@function tint-color($color, $amount) {
  @if meta.type-of($color) != "color" {
    @return throw.parameter-type("tint-color", "color", $color, false, "color");
  }

  @if meta.type-of($amount) != "number" {
    @return throw.parameter-type(
      "tint-color",
      "amount",
      $amount,
      false,
      "number"
    );
  }

  @return color.mix(#fff, $color, $amount);
}

// ❌ Try the result with Invalid input
@debug tint-color(true, "one");

// ✅ Try the result with Valid input
@debug tint-color(#c69, 90%);
```

<p>Otherwise,</p>

```scss
@use "sass:meta";
@use "sass:color";

@function tint-color($color, $amount) {
  @if meta.type-of($color) != "color" {
    @return parameter-type-exception(
      "tint-color",
      "color",
      $color,
      false,
      "color"
    );
  }

  @if meta.type-of($amount) != "number" {
    @return parameter-type-exception(
      "tint-color",
      "amount",
      $amount,
      false,
      "number"
    );
  }

  @return color.mix(#fff, $color, $amount);
}

// ❌ Try the result with Invalid input
@debug tint-color(true, "one");

// ✅ Try the result with Valid input
@debug tint-color(#c69, 90%);
```

<h1>Packages</h1>

<h2><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package">Throw Package</a></h2>
<p>Provides Sass mixins and functions to standardize exception messages.</p>

<h3>Mixins</h3>
<dl>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#exception-mixin">Exception</a></dt>
   <dd>Use in place of <code>@error</code> statements inside mixins or other control structures with CSS output (not functions).</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#variable-mixin">Variable</a></dt>
   <dd>Use in place of variable <code>@error</code> statements inside mixins or other control structures with CSS output (not functions).</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#variable-type-mixin">Variable Type</a></dt>
   <dd>Use in place of variable type <code>@error</code> statements inside mixins or other control structures with CSS output (not functions).</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#parameter-mixin">Parameter</a></dt>
   <dd>Use in place of parameter <code>@error</code> statements inside mixins or other control structures with CSS output (not functions).</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#parameter-type-mixin">Parameter Type</a></dt>
   <dd>Use in place of parameter type <code>@error</code> statements inside mixins or other control structures with CSS output (not functions).</dd>
</dl>

<h3>Function</h3>
<dl>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#exception-function">Exception</a></dt>
   <dd>Use in place of <code>@error</code> statements inside functions.</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#variable-function">Variable</a></dt>
   <dd>Returns an error message stating an issue with one or more variables.</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#variable-type-function">Variable Type</a></dt>
   <dd>Returns an error message stating a variable received the wrong type.</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#parameter-function">Parameter</a></dt>
   <dd>Returns an error message stating an issue with one or more parameters.</dd>
   <dt><a href="https://github.com/officialxviid/sasses/wiki/Throw-Package#parameter-type-function">Parameter Type</a></dt>
   <dd>Returns an error message stating a parameter received the wrong type.</dd>
</dl>
