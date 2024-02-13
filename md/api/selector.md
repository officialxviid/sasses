<h1 align="center">
    <img alt="logo" width="70" src="../../logo.png"/><br>
    Selector Module
</h1>

<p align="center">
    Provides access to Sass’s powerful selector engine.
</p>

<p align="center">
  <img alt="Dart Sass" src="https://img.shields.io/badge/Dart%20Sass-since%201.23.0-green"/>&nbsp;<img alt="LibSass" src="https://img.shields.io/badge/LibSass-%E2%9C%97-red"/>&nbsp;<img alt="Ruby Sass" src="https://img.shields.io/badge/Ruby%20Sass-%E2%9C%97-red"/>
</p>

<p align="center"><code>@use "sasses/selector"</code></p>

<h2>Table of Contents</h2>
<p>
    <ul>
        <li>
            <a href="#functions">Functions</a>
            <ul>
                <li><a href="#is-superselector">Is Superselector</a></li>
                <li><a href="#append">Append</a></li>
                <li><a href="#extend">Extend</a></li>
                <li><a href="#nest">Nest</a></li>
                <li><a href="#parse">Parse</a></li>
                <li><a href="#replace">Replace</a></li>
                <li><a href="#unify">Unify</a></li>
                <li><a href="#simple-selectors">Simple Selectors</a></li>
            </ul>
        </li>
    </ul>
</p>

<h2>Functions</h2>

<h3>Is Superselector</h3>

```sass
selector.is-superselector($super, $sub)  //=> boolean

// or

is-superselector($super, $sub)  //=> boolean
```

<p>Returns whether the selector <code>$super</code> matches all the elements that the selector <code>$sub</code> matches.</p>
<p>Still returns true even if <code>$super</code> matches <i>more</i> elements than <code>$sub</code>.</p>
<p>The <code>$super</code> and <code>$sub</code> selectors may contain <a target="_blank" href="https://sass-lang.com/documentation/style-rules/placeholder-selectors/">placeholder selectors</a>, but not <a target="_blank" href="https://sass-lang.com/documentation/style-rules/parent-selector/">parent selectors</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.is-superselector("a", "a.disabled")  //=> true
> @debug selector.is-superselector("a.disabled", "a")  //=> false
> @debug selector.is-superselector("a", "sidebar a")  //=> true
> @debug selector.is-superselector("sidebar a", "a")  //=> false
> @debug selector.is-superselector("a", "a")  //=> true
> ```

<h3>Append</h3>

```sass
selector.append($selectors...)  //=> selector

// or

selector-append($selectors...)  //=> selector
```

<p>Combines <code>$selectors</code> without <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator">descendant combinators</a>—that is, without whitespace between them.</p>
<p>If any selector in <code>$selectors</code> is a selector list, each complex selector is combined separately.</p>
<p>The <code>$selectors</code> may contain <a target="_blank" href="https://sass-lang.com/documentation/style-rules/placeholder-selectors/">placeholder selectors</a>, but not <a target="_blank" href="https://sass-lang.com/documentation/style-rules/parent-selector/">parent selectors</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.append("a", ".disabled")  //=> a.disabled
> @debug selector.append(".accordion", "__copy")  //=> .accordion__copy
> @debug selector.append(".accordion", "__copy, __image")  //=> .accordion__copy, .accordion__image
> ```

<h3>Extend</h3>

```sass
selector.extend($selector, $extendee, $extender)  //=> selector

// or

selector-extend($selector, $extendee, $extender)  //=> selector
```

<p>Extends <code>$selector</code> as with the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/extend/"><code>@extend</code> rule</a>.</p>
<p>Returns a copy of <code>$selector</code> modified with the following <a target="_blank" href="https://sass-lang.com/documentation/at-rules/extend/"><code>@extend</code> rule</a>:</p>

```sass
#{$extender} {
  @extend #{$extendee};
}
```

<p>In other words, replaces all instances of <code>$extendee</code> in <code>$selector</code> with <code>$extendee</code>, <code>$extender</code>. If <code>$selector</code> doesn’t contain <code>$extendee</code>, returns it as-is.</p>
<p>The <code>$selector</code>, <code>$extendee</code>, and <code>$extender</code> selectors may contain <a target="_blank" href="https://sass-lang.com/documentation/style-rules/placeholder-selectors/">placeholder selectors</a>, but not <a target="_blank" href="https://sass-lang.com/documentation/style-rules/parent-selector/">parent selectors</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.extend("a.disabled", "a", ".link")  //=> a.disabled, .link.disabled
> @debug selector.extend("a.disabled", "h1", "h2")  //=> a.disabled
> @debug selector.extend(".guide .info", ".info", ".content nav.sidebar")
> //=> .guide .info, .guide .content nav.sidebar, .content .guide nav.sidebar
> ```

<h3>Nest</h3>

```sass
selector.nest($selectors...)  //=> selector

// or

selector-nest($selectors...)  //=> selector
```

<p>Combines <code>$selectors</code> as though they were nested within one another in the stylesheet.</p>
<p>The <code>$selectors</code> may contain placeholder selectors. Unlike other selector functions, all of them except the first may also contain <a target="_blank" href="https://sass-lang.com/documentation/style-rules/parent-selector/">parent selectors</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.nest("ul", "li")  //=> ul li
> @debug selector.nest(".alert, .warning", "p")  //=> .alert p, .warning p
> @debug selector.nest(".alert", "&:hover")  //=> .alert:hover
> @debug selector.nest(".accordion", "&__copy")  //=> .accordion__copy
> ```

<h3>Parse</h3>

```sass
selector.parse($selector)  //=> selector

// or

selector-parse($selector)  //=> selector
```

<p>Returns <code>$selector</code> in the selector value format.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.parse(".main aside:hover, .sidebar p")
> // ((unquote(".main") unquote("aside:hover")),
> //  (unquote(".sidebar") unquote("p")))
> ```

<h3>Replace</h3>

```sass
selector.replace($selector, $original, $replacement)  //=> selector

// or

selector-replace($selector, $original, $replacement)  //=> selector
```

<p>Returns a copy of <code>$selector</code> with all instances of <code>$original</code> replaced by <code>$replacement</code>.</p>
<p>This uses the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/extend/"><code>@extend</code> rule</a>’s intelligent unification to make sure <code>$replacement</code> is seamlessly integrated into <code>$selector</code>. If <code>$selector</code> doesn’t contain <code>$original</code>, returns it as-is.</p>
<p>The <code>$selector</code>, <code>$original</code>, and <code>$replacement</code> selectors may contain <a target="_blank" href="https://sass-lang.com/documentation/style-rules/placeholder-selectors/">placeholder selectors</a>, but not <a target="_blank" href="https://sass-lang.com/documentation/style-rules/parent-selector/">parent selectors</a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.replace("a.disabled", "a", ".link")  //=> .link.disabled
> @debug selector.replace("a.disabled", "h1", "h2")  //=> a.disabled
> @debug selector.replace(".guide .info", ".info", ".content nav.sidebar")
> //=> .guide .content nav.sidebar, .content .guide nav.sidebar
> ```

<h3>Unify</h3>

```sass
selector.unify($selector1, $selector2)  //=> selector | null

// or

selector-unify($selector1, $selector2)  //=> selector | null
```

<p>Returns a selector that matches only elements matched by <i>both</i> <code>$selector1</code> and <code>$selector2</code>.</p>
<p>Returns <code>null</code> if <code>$selector1</code> and <code>$selector2</code> don’t match any of the same elements, or if there’s no selector that can express their overlap.</p>
<p>Like selectors generated by the <a target="_blank" href="https://sass-lang.com/documentation/at-rules/extend/"><code>@extend</code> rule</a>, the returned selector isn’t guaranteed to match <i>all</i> the elements matched by both <code>$selector1</code> and <code>$selector2</code> if they’re both complex selectors.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.unify("a", ".disabled")  //=> a.disabled
> @debug selector.unify("a.disabled", "a.outgoing")  //=> a.disabled.outgoing
> @debug selector.unify("a", "h1")  //=> null
> @debug selector.unify(".warning a", "main a")  //=> .warning main a, main .warning a
> ```

<h3>Simple Selectors</h3>

```sass
selector.simple-selectors($selector)  //=> list

// or

simple-selectors($selector)  //=> list
```

<p>Returns a list of simple selectors in <code>$selector</code>.</p>
<p>The <code>$selector</code> must be a single string that contains a compound selector. This means it may not contain combinators (including spaces) or commas.</p>
<p>The returned list is comma-separated, and the simple selectors are unquoted strings.</p>

> **Sass**
>
> ```sass
> @use "sasses/selector"
>
> @debug selector.simple-selectors("a.disabled")  //=> a, .disabled
> @debug selector.simple-selectors("main.blog:after")  //=> main, .blog, :after
> ```
