<h1 align="center">
    <img alt="logo" width="70" src="../../logo.png"/><br>
    Meta Module
</h1>

<p align="center">
    Exposes the advanced details of Sass’s inner workings.
</p>

<p align="center">
  <img alt="Dart Sass" src="https://img.shields.io/badge/Dart%20Sass-since%201.23.0-green"/>&nbsp;<img alt="LibSass" src="https://img.shields.io/badge/LibSass-%E2%9C%97-red"/>&nbsp;<img alt="Ruby Sass" src="https://img.shields.io/badge/Ruby%20Sass-%E2%9C%97-red"/>
</p>

<p align="center"><code>@use "sasses/meta"</code></p>

<h2>Table of Contents</h2>
<p>
    <ul>
        <li>
            <a href="#mixins">Mixins</a>
            <ul>
                <li><a href="#apply">Apply</a></li>
                <li><a href="#load-css">Load CSS</a></li>
            </ul>
        </li>
        <li>
            <a href="#functions">Functions</a>
            <ul>
                <li><a href="#accepts-content">Accepts Content</a></li>
                <li><a href="#calc-arguments">Calc Arguments</a></li>
                <li><a href="#calc-name">Calc name</a></li>
                <li><a href="#call">Call</a></li>
                <li><a href="#content-exists">Content Exists</a></li>
                <li><a href="#feature-exists">Feature Exists</a></li>
                <li><a href="#function-exists">Function Exists</a></li>
                <li><a href="#get-function">Get function</a></li>
                <li><a href="#get-mixin">Get mixin</a></li>
                <li><a href="#global-variable-exists">Global Variable Exists</a></li>
                <li><a href="#inspect">Inspect</a></li>
                <li><a href="#keywords">Keywords</a></li>
                <li><a href="#mixin-exists">Mixin Exists</a></li>
                <li><a href="#module-functions">Module Functions</a></li>
                <li><a href="#module-mixins">Module Mixins</a></li>
                <li><a href="#module-variables">Module Variables</a></li>
                <li><a href="#type-of">Type of</a></li>
                <li><a href="#variable-exists">Variable Exists</a></li>
            </ul>
        </li>
    </ul>
</p>

<h2>Mixins</h2>

<h3>Apply</h3>

```sass
meta.apply($mixin, $args...)
```

<p>Includes <code>$mixin</code> with <code>$args</code>. If this is passed a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/mixin/#content-blocks"><code>@content</code> block</a>, it’s forwarded to <code>$mixin</code>.</p>
<p>The <code>$mixin</code> must be a <a target="_blank" href="https://sass-lang.com/documentation/values/mixins/">mixin value</a>, such as one returned by <a href="#get-mixin"><code>meta.get-mixin()</code></a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/meta"
> @use "sass:string"
>
> /// Passes each element of $list to a separate invocation of $mixin.
> @mixin apply-to-all($mixin, $list)
>   @each $element in $list
>     @include meta.apply($mixin, $element)
>
> @mixin font-class($size)
>   .font-#{$size}
>     font-size: $size
>
>
> $sizes: 8px, 12px 2rem
>
> @include apply-to-all(meta.get-mixin("font-class"), $sizes)
> ```
>
> **CSS**
>
> ```css
> .font-8px {
>   font-size: 8px;
> }
>
> .font-12px {
>   font-size: 12px;
> }
>
> .font-2rem {
>   font-size: 2rem;
> }
> ```

<h3>Load CSS</h3>

```sass
meta.load-css($url, $with: null)
```

<p>Loads the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/">module</a> at <code>$url</code> and includes its CSS as though it were written as the contents of this mixin. The <code>$with</code> parameter provides <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/#configuration">configuration</a> for the modules; if it’s passed, it must be a map from variable names (without $) to the values of those variables to use in the loaded module.</p>
<p>If <code>$url</code> is relative, it’s interpreted as relative to the file in which <code>meta.load-css()</code> is included.</p>
<p>
    <b>Like the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a>:</b>
    <ul>
        <li>This will only evaluate the given module once, even if it’s loaded multiple times in different ways.</li>
        <li>This cannot provide configuration to a module that’s already been loaded, whether or not it was already loaded with configuration.</li>
    </ul>
</p>
<p>
    <b>Unlike the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a>:</b>
    <ul>
        <li>This doesn’t make any members from the loaded module available in the current module.</li>
        <li>This can be used anywhere in a stylesheet. It can even be nested within style rules to create nested styles!</li>
        <li>The module URL being loaded can come from a variable and include <a target="_blank" href="https://sass-lang.com/documentation/interpolation/">interpolation</a>.</li>
    </ul>
</p>

> **Sass**
>
> ```sass
> // dark-theme/_code.sass
> $border-contrast: false !default
>
> code
>   background-color: #6b717f
>   color: #d2e1dd
>   @if $border-contrast
>       border-color: #dadbdf
> ```
>
> ```sass
> // style.sass
> @use "sasses/meta"
>
> body.dark
>   $configuration: ("border-contrast": true)
>   @include meta.load-css("dark-theme/code", $with: $configuration)
> ```
>
> **CSS**
>
> ```css
> body.dark code {
>   background-color: #6b717f;
>   color: #d2e1dd;
>   border-color: #dadbdf;
> }
> ```

<h2>Functions</h2>

<h3>Accepts Content</h3>

```sass
meta.accepts-content($mixin)  //=> boolean
```

<p>Returns whether the given mixin value can accept a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/mixin/#content-blocks"><code>@content</code> block</a>.</p>
<p>This returns true if it's <i>possible</i> for the mixin to accept a <code>@content</code> block, even if it doesn't always do so.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
>
> @mixin yes
>     @content
>
> @mixin no
>     .font-size-18px
>         font-size: 18px
>
>
> $check1: meta.get-mixin(yes)
> $check2: meta.get-mixin(no)
>
> @debug meta.accepts-content($check1)  //=> true
> @debug meta.accepts-content($check2)  //=> false
> ```

<h3>Calc Arguments</h3>

```sass
meta.calc-args($calc)  //=> list
```

<p>Returns the arguments for the given <a target="_blank" href="https://sass-lang.com/documentation/values/calculations/">calculation</a>.</p>
<p>If an argument is a number or a nested calculation, it's returned as that type. Otherwise, it's returned as an unquoted string.</p>

> **Sass**
>
> ```sass
> @use "sasses/meta"
>
> @debug meta.calc-args(calc(100px + 10%))  //=> unquote("100px + 10%")
> @debug meta.calc-args(clamp(50px, var(--width), 1000px))  //=> 50px, unquote("var(--width)"), 1000px
> ```

<h3>Calc Name</h3>

```sass
meta.calc-name($calc)  //=> quoted string
```

<p>Returns the name of the given <a target="_blank" href="https://sass-lang.com/documentation/values/calculations/">calculation</a>.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @debug meta.calc-name(calc(100px + 10%))  //=> "calc"
> @debug meta.calc-name(clamp(50px, var(--width), 1000px))  //=> "clamp"
> ```

<h3>Call</h3>

```sass
meta.call($function, $args...)
```

<p>Invokes <code>$function</code> with <code>$args</code> and returns the result.</p>
<p>The <code>$function</code> must be a <a target="_blank" href="https://sass-lang.com/documentation/values/functions/">function value</a>, such as one returned by <a href="#get-function"><code>meta.get-function()</code></a>.</p>

> **Sass**
>
> ```sass
> @use "sass:list"
> @use 'sasses/meta'
> @use "sass:string"
>
> /// Return a copy of $list with all elements for which $condition returns `true`
> /// removed.
> @function remove-where($list, $condition)
>   $new-list: ()
>   $separator: list.separator($list)
>   @each $element in $list
>       @if not meta.call($condition, $element)
>           $new-list: list.append($new-list, $element, $separator: $separator)
>   @return $new-list
>
> $fonts: Tahoma, Geneva, "Helvetica Neue", Helvetica, Arial, sans-serif
>
> .content
>   @function contains-helvetica($string)
>       @return string.index($string, "Helvetica")
>   font-family: remove-where($fonts, meta.get-function("contains-helvetica"))
> ```
>
> **CSS**
>
> ```css
> .content {
>   font-family: Tahoma, Geneva, Arial, sans-serif;
> }
> ```

<h3>Content Exists</h3>

```sass
meta.content-exists()  //=> boolean
```

<p>Returns whether the current mixin was passed a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/mixin/#content-blocks"><code>@content</code> block</a>.</p>
<p>Throws an error if called outside of a mixin.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @mixin debug-content-exists
>   @debug meta.content-exists()
>   @content
>
> @include debug-content-exists  //=> false
> @include debug-content-exists  //=> true
> ```

<h3>Feature Exists</h3>

```sass
meta.feature-exists($feature)  //=> boolean
```

<p>Returns whether the current Sass implementation supports $feature.</p>
<p>
    The $feature must be a string. The currently recognized features are:
    <ul>
        <li><code>global-variable-shadowing</code>, which means that a local variable will <a target="_blank" href="https://sass-lang.com/documentation/variables/#shadowing">shadow</a> a global variable unless it has the <code>!global</code> flag.</li>
        <li><code>extend-selector-pseudoclass</code>, which means that the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/extend/"><code>@extend</code> rule</a> will affect selectors nested in pseudo-classes like <code>:not()</code>.</li>
        <li><code>units-level3</code>, which means that unit arithmetic supports units defined in <a target="_blank" href="https://www.w3.org/TR/css3-values/">CSS Values and Units Level 3</a>.</li>
        <li><code>at-error</code>, which means that the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/error/"><code>@error</code> rule</a> is supported.</li>
        <li><code>custom-property</code>, which means that <a target="_blank" href="https://sass-lang.com/documentation/style-rules/declarations/#custom-properties">custom property declaration</a> values don't support any <a target="_blank" href="https://sass-lang.com/documentation/syntax/structure/#expressions">expressions</a> other than <a target="_blank" href="https://sass-lang.com/documentation/interpolation/">interpolation</a>.</li>
    </ul>
</p>
<p>Returns <code>false</code> for any unrecognized <code>$feature</code>.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @debug meta.feature-exists("at-error")  //=> true
> @debug meta.feature-exists("unrecognized")  //=> false
> ```

<h3>Function Exists</h3>

```sass
meta.function-exists($name, $module: null)  //=> boolean
```

<p>Returns whether a function named <code>$name</code> is defined, either as a built-in function or a user-defined function.</p>
<p>If <code>$module</code> is passed, this also checks the module named <code>$module</code> for the function definition. <code>$module</code> must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @debug meta.function-exists("div", "math")  //=> true
> @debug meta.function-exists("scale-color")  //=> true
> @debug meta.function-exists("add")  //=> false
>
> @function add($num1, $num2)
>   @return $num1 + $num2
>
> @debug meta.function-exists("add")  //=> true
> ```

<h3>Fet Function</h3>

```sass
meta.get-function($name, $css: false, $module: null)  //=> function
```

<p>Returns the <a target="_blank" href="https://sass-lang.com/documentation/values/functions/">function value</a> named <code>$name</code>.</p>
<p>If <code>$module</code> is <code>null</code>, this returns the function named <code>$name</code> without a namespace (including <a target="_blank" href="https://sass-lang.com/documentation/modules/#global-functions">global built-in functions</a>). Otherwise, <code>$module</code> must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file, in which case this returns the function in that module named <code>$name</code>.</p>
<p>By default, this throws an error if <code>$name</code> doesn't refer to Sass function. However, if <code>$css</code> is <code>true</code>, it instead returns a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/function/#plain-css-functions">plain CSS function</a>.</p>
<p>The returned mixin can be included using <a target="_blank" href="#apply"><code>meta.apply()</code></a>.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
> @use "sass:string"
>
> /// Passes each element of $list to a separate invocation of $mixin.
> @mixin apply-to-all($mixin, $list)
>   @each $element in $list
>       @include meta.apply($mixin, $element)
>
> @mixin font-class($size)
>   .font-#{$size}
>       font-size: $size
>
>
> $sizes: 8px, 12px 2rem
>
> @include apply-to-all(meta.get-mixin("font-class"), $sizes)
> ```

<h3>Get Mixin</h3>

```sass
meta.get-mixin($name, $module: null)  //=> function
```

<p>Returns the mixin value named <code>$name</code>.</p>
<p>If <code>$module</code> is <code>null</code>, this returns the mixin named <code>$name</code> defined in the current module. Otherwise, <code>$module</code> must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file, in which case this returns the mixin in that module named <code>$name</code>.</p>
<p>By default, this throws an error if <code>$name</code> doesn't refer to a mixin. However, if <code>$css</code> is <code>true</code>, it instead returns a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/function/#plain-css-functions">plain CSS function</a>.</p>
<p>The returned function can be called using <a href="#call"><code>meta.call()</code></a>.</p>

> **Sass**
>
> ```sass
> @use "sass:list"
> @use 'sasses/meta'
> @use "sass:string"
>
> /// Return a copy of $list with all elements for which $condition returns `true`
> /// removed.
> @function remove-where($list, $condition)
>   $new-list: ()
>   $separator: list.separator($list)
>   @each $element in $list
>       @if not meta.call($condition, $element)
>           $new-list: list.append($new-list, $element, $separator: $separator)
>   @return $new-list
>
>
> $fonts: Tahoma, Geneva, "Helvetica Neue", Helvetica, Arial, sans-serif
>
> .content
>   @function contains-helvetica($string)
>       @return string.index($string, "Helvetica")
>   font-family: remove-where($fonts, meta.get-function("contains-helvetica"))
> ```
>
> **CSS**
>
> ```css
> .content {
>   font-family: Tahoma, Geneva, Arial, sans-serif;
> }
> ```

<h3>Global Variable Exists</h3>

```sass
meta.global-variable-exists($name, $module: null)  //=> boolean
```

<p>Returns whether a <a target="_blank" href="https://sass-lang.com/documentation/variables/#scope">global variable</a> named <code>$name</code> (without the $) exists.</p>
<p>If <code>$module</code> is <code>null</code>, this returns whether a variable named <code>$name</code> without a namespace exists. Otherwise, <code>$module</code> must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file, in which case this returns whether that module has a variable named <code>$name</code>.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @debug meta.global-variable-exists("var1")  //=> false
>
> $var1: value
> @debug meta.global-variable-exists("var1")  //=> true
>
> h1
>   // $var2 is local.
>   $var2: value
>   @debug meta.global-variable-exists("var2")  //=> false
> ```

<h3>Inspect</h3>

```sass
meta.inspect($value)  //=> unquoted string
```

<p>Returns a string representation of <code>$value</code>.</p>
<p>Returns a representation of <i>any</i> Sass value, not just those that can be represented in CSS. As such, its return value is not guaranteed to be valid CSS.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @debug meta.inspect(10px 20px 30px)  //=> unquote("10px 20px 30px")
> @debug meta.inspect(("width": 200px))  //=> unquote('("width": 200px)')
> @debug meta.inspect(null)  //=> unquote("null")
> @debug meta.inspect("Helvetica")  //=> unquote('"Helvetica"')
> ```

<h3>Keywords</h3>

```sass
meta.keywords($args)  //=> map
```

<p>Returns the keywords passed to a mixin or function that takes <a target="_blank" href="https://sass-lang.com/documentation/at-rules/mixin/#taking-arbitrary-arguments">arbitrary arguments</a>. The <code>$args</code> argument must be an <a target="_blank" href="https://sass-lang.com/documentation/values/lists/#argument-lists">argument list</a>.</p>
<p>The keywords are returned as a map from argument names as unquoted strings (not including $) to the values of those arguments.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @mixin syntax-colors($args...)
>   @debug meta.keywords($args)
>   // (string: #080, comment: #800, variable: #60b)
>
>   @each $name, $color in meta.keywords($args)
>       pre span.stx-#{$name}
>           color: $color
>
>
> @include syntax-colors($string: #080, $comment: #800, $variable: #60b)
> ```
>
> **CSS**
>
> ```css
> pre span.stx-string {
>   color: #080;
> }
>
> pre span.stx-comment {
>   color: #800;
> }
>
> pre span.stx-variable {
>   color: #60b;
> }
> ```

<h3>Mixin Exists</h3>

```sass
meta.mixin-exists($name, $module: null)  //=> boolean
```

<p>Returns whether a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/mixin/">mixin</a> named <code>$name</code> exists.</p>
<p>If <code>$module</code> is null, this returns whether a mixin named <code>$name</code> without a namespace exists. Otherwise, <code>$module</code> must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file, in which case this returns whether that module has a mixin named <code>$name</code>.</p>

> **Sass**
>
> ```sass
> @use 'sasses/meta'
>
> @debug meta.mixin-exists("shadow-none")  //=> false
>
> @mixin shadow-none
>   box-shadow: none
>
> @debug meta.mixin-exists("shadow-none")  //=> true
> ```

<h3>Module Functions</h3>

```sass
meta.module-functions($module)  //=> map
```

<p>Returns all the functions defined in a module, as a map from function names to <a target="_blank" href="https://sass-lang.com/documentation/values/functions/">function values</a>.</p>
<p>The <code>$module</code> parameter must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file.</p>

> **Sass**
>
> ```sass
> // _functions.sass
> @function pow($base, $exponent)
>   $result: 1
>   @for $_ from 1 through $exponent
>       $result: $result * $base
>   @return $result
> ```
>
> ```sass
> @use "sass:map"
> @use 'sasses/meta'
> @use "functions"
>
> @debug meta.module-functions("functions")  //=> ("pow": get-function("pow"))
>
> @debug meta.call(map.get(meta.module-functions("functions"), "pow"), 3, 4)  //=> 81
> ```

<h3>Module Mixins</h3>

```sass
meta.module-mixins($module)  //=> map
```

<p>Returns all the mixins defined in a module, as a map from mixin names to <a target="_blank" href="https://sass-lang.com/documentation/values/mixins/">mixin values</a>.</p>
<p>The <code>$module</code> parameter must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file.</p>

> **Sass**
>
> ```sass
> // _mixins.scss
> @mixin stretch()
>   align-items: stretch
>   display: flex
>   flex-direction: row
> ```
>
> ```sass
> @use "sass:map"
> @use 'sasses/meta'
>
> @use "mixins"
>
> @debug meta.module-mixins("mixins")  //=> ("stretch": get-mixin("stretch"))
>
> .header
>   @include meta.apply(map.get(meta.module-mixins("mixins"), "stretch"))
> ```
>
> **CSS**
>
> ```css
> .header {
>   align-items: stretch;
>   display: flex;
>   flex-direction: row;
> }
> ```

<h3>Module Variables</h3>

```sass
meta.module-variables($module)  //=> map
```

<p>Returns all the variables defined in a module, as a map from variable names (without $) to the values of those variables.</p>
<p>The <code>$module</code> parameter must be a string matching the namespace of a <a target="_blank" href="https://sass-lang.com/documentation/at-rules/use/"><code>@use</code> rule</a> in the current file.</p>

> **Sass**
>
> ```sass
> // _variables.sass
> $hopbush: #c69
> $midnight-blue: #036
> $wafer: #e1d7d2
> ```
>
> ```sass
> @use "sasses/meta"
>
> @use "variables"
>
> @debug meta.module-variables("variables")
> // (
> //    "hopbush": #c69,
> //    "midnight-blue": #036,
> //    "wafer": #e1d7d2
> // )
> ```

<h3>Type of</h3>

```sass
meta.type-of($value)  //=> unquoted string
```

<p>Returns the type of <code>$value</code>.</p>
<p>
    This can return the following values:
    <ul>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/numbers/">number</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/strings/">string</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/colors/">color</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/lists/">list</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/maps/">map</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/calculations/">calculation</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/booleans/">bool</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/null/">null</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/functions/">function</a></li>
        <li><a target="_blank" href="https://sass-lang.com/documentation/values/lists/#argument-lists">arglist</a></li>
    </ul>
</p>
<p>New possible values may be added in the future. It may return either <code>list</code> or <code>map</code> for (), depending on whether or not it was returned by a <a target="_blank" href="https://sass-lang.com/documentation/modules/map/">map function</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/meta"
>
> @debug meta.type-of(10px)  //=> number
> @debug meta.type-of(10px 20px 30px)  //=> list
> @debug meta.type-of(())  //=> list
> ```

<h3>Variable Exists</h3>

```sass
meta.variable-exists($name)  //=> boolean
```

<p>Returns whether a variable named <code>$name</code> (without the $) exists in the current scope.</p>

> **Sass**
>
> ```sass
> @use "sasses/meta"
>
> @debug meta.variable-exists("var1")  //=> false
>
> $var1: value
> @debug meta.variable-exists("var1")  //=> true
>
> h1
>   // $var2 is local.
>   $var2: value
>   @debug meta.variable-exists("var2")  //=> true
> ```
