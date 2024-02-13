<h1 align="center">
    <img alt="logo" width="70" src="../../logo.png"/><br>
    Color Module
</h1>

<p align="center">
    Generates new colors based on existing ones, making it easy to build color themes.
</p>

<p align="center">
  <img alt="Dart Sass" src="https://img.shields.io/badge/Dart%20Sass-since%201.23.0-green"/>&nbsp;<img alt="LibSass" src="https://img.shields.io/badge/LibSass-%E2%9C%97-red"/>&nbsp;<img alt="Ruby Sass" src="https://img.shields.io/badge/Ruby%20Sass-%E2%9C%97-red"/>
</p>

<p align="center"><code>@use "sasses/color"</code></p>

<h2>Table of Contents</h2>
<p>
    <ul>
        <li>
            <a href="#functions">Functions</a>
            <ul>
                <li><a href="#adjust">Adjust</a></li>
                <li><a href="#adjust-hue">Adjust Hue</a></li>
                <li><a href="#alpha">Alpha</a></li>
                <li><a href="#opacity">Opacity</a></li>
                <li><a href="#blackness">Blackness</a></li>
                <li><a href="#blue">Blue</a></li>
                <li><a href="#change">Change</a></li>
                <li><a href="#complement">Complement</a></li>
                <li><a href="#darken">Darken</a></li>
                <li><a href="#desaturate">Desaturate</a></li>
                <li><a href="#grayscale">Grayscale</a></li>
                <li><a href="#green">Green</a></li>
                <li><a href="#hue">Hue</a></li>
                <li><a href="#hue-whiteness-blackness-hwb">Hue Whiteness Blackness (HWB)</a></li>
                <li><a href="#ie-hex-str">IE HEX Str</a></li>
                <li><a href="#invert">Invert</a></li>
                <li><a href="#lighten">Lighten</a></li>
                <li><a href="#lightness">Lightness</a></li>
                <li><a href="#mix">Mix</a></li>
                <li><a href="#opacify">Opacify</a></li>
                <li><a href="#fade-in">Fade In</a></li>
                <li><a href="#red">Red</a></li>
                <li><a href="#saturate">Saturate</a></li>
                <li><a href="#saturation">Saturation</a></li>
                <li><a href="#scale">Scale</a></li>
                <li><a href="#transparentize">Transparentize</a></li>
                <li><a href="#fade-out">Fade Out</a></li>
                <li><a href="#whiteness">Whiteness</a></li>
            </ul>
        </li>
    </ul>
</p>

<h2>Functions</h2>

<h3>Adjust</h3>

```sass
color.adjust($color,
  $red: null, $green: null, $blue: null,
  $hue: null, $saturation: null, $lightness: null,
  $whiteness: null, $blackness: null,
  $alpha: null
)  //=> color

// or

adjust-color(...)  //=> color
```

<p>Increases or decreases one or more properties of <code>$color</code> by fixed amounts.</p>
<p>Adds the value passed for each keyword argument to the corresponding property of the color, and returns the adjusted color. It’s an error to specify an RGB property (<code>$red</code>, <code>$green</code>, and/or <code>$blue</code>) at the same time as an HSL property (<code>$hue</code>, <code>$saturation</code>, and/or <code>$lightness</code>), or either of those at the same time as an HWB property (<code>$hue</code>, <code>$whiteness</code>, and/or <code>$blackness</code>).</p>
<p>All optional arguments must be numbers. The <code>$red</code>, <code>$green</code>, and <code>$blue</code> arguments must be unitless and between -255 and 255 (inclusive). The <code>$hue</code> argument must have either the unit deg or no unit. The <code>$saturation</code>, <code>$lightness</code>, <code>$whiteness</code>, and <code>$blackness</code> arguments must be between -100% and 100% (inclusive), and may not be unitless. The <code>$alpha</code> argument must be unitless and between -1 and 1 (inclusive).</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.adjust(#6b717f, $red: 15)  //=> #7a717f
> @debug color.adjust(#d2e1dd, $red: -10, $blue: 10)  //=> #c8e1e7
> @debug color.adjust(#998099, $lightness: -30%, $alpha: -0.4)  //=> rgba(71, 57, 71, 0.6)
> ```

<h3>Adjust Hue</h3>

```sass
adjust-hue($color, $degrees)  //=> color
```

<p>Increases or decreases <code>$color</code>’s hue.</p>
<p>The $hue must be a number between <code>-360deg</code> and <code>360deg</code> (inclusive) to add to <code>$color</code>’s hue. It may be <a target="_blank" href="https://sass-lang.com/documentation/values/numbers/#units">unitless</a> but it may not have any unit other than <code>deg</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> // Hue 222deg becomes 282deg.
> @debug adjust-hue(#6b717f, 60deg)  //=> #796b7f
>
> // Hue 164deg becomes 104deg.
> @debug adjust-hue(#d2e1dd, -60deg)  //=> #d6e1d2
>
> // Hue 210deg becomes 255deg.
> @debug adjust-hue(#036, 45)  //=> #1a0066
> ```

<h3>Alpha</h3>

```sass
color.alpha($color)  //=> number
alpha($color)  //=> number
```

<p>Returns the alpha channel of <code>$color</code> as a number between 0 and 1.</p>
<p>As a special case, this supports the Internet Explorer syntax <code>alpha(opacity=20)</code>, for which it returns an unquoted string.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.alpha(#e1d7d2)  //=> 1
> @debug color.opacity(rgb(210, 225, 221, 0.4))  //=> 0.4
> ```

<h3>Opacity</h3>

```sass
opacity($color)  //=> number
```

<p>Returns the alpha channel of <code>$color</code> as a number between 0 and 1.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug opacity(#fff)  //=> 1
> @debug opacity(#fefefe)  //=> 1
> ```

<h3>Blackness</h3>

```sass
color.blackness($color)  //=> number
```

<p>Returns the HWB blackness of <code>$color</code> as a number between 0% and 100%.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.blackness(#e1d7d2)  //=> 11.7647058824%
> @debug color.blackness(white)  //=> 0%
> @debug color.blackness(black)  //=> 100%
> ```

<h3>Blue</h3>

```sass
color.blue($color)  //=> number

// or

blue($color)  //=> number
```

<p>Returns the blue channel of <code>$color</code> as a number between 0 and 255.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.blue(#e1d7d2)  //=> 210
> @debug color.blue(white)  //=> 255
> @debug color.blue(black)  //=> 0
> ```

<h3>Change</h3>

```sass
color.change($color,
  $red: null, $green: null, $blue: null,
  $hue: null, $saturation: null, $lightness: null,
  $whiteness: null, $blackness: null,
  $alpha: null
)  //=> color

// or

change-color(...)  //=> color
```

<p>Sets one or more properties of a color to new values.</p>
<p>Uses the value passed for each keyword argument in place of the corresponding property of the color, and returns the changed color. It’s an error to specify an RGB property (<code>$red</code>, <code>$green</code>, and/or <code>$blue</code>) at the same time as an HSL property (<code>$hue</code>, <code>$saturation</code>, and/or <code>$lightness</code>), or either of those at the same time as an HWB property (<code>$hue</code>, <code>$whiteness</code>, and/or <code>$blackness</code>).</p>
<p>All optional arguments must be numbers. The <code>$red</code>, <code>$green</code>, and <code>$blue</code> arguments must be unitless and between 0 and 255 (inclusive). The <code>$hue</code> argument must have either the unit deg or no unit. The <code>$saturation</code>, <code>$lightness</code>, <code>$whiteness</code>, and <code>$blackness</code> arguments must be between 0% and 100% (inclusive), and may not be unitless. The <code>$alpha</code> argument must be unitless and between 0 and 1 (inclusive).</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.change(#6b717f, $red: 100)  //=> #64717f
> @debug color.change(#d2e1dd, $red: 100, $blue: 50)  //=> #64e132
> @debug color.change(#998099, $lightness: 30%, $alpha: 0.5)  //=> rgba(85, 68, 85, 0.5)
> ```

<h3>Complement</h3>

```sass
color.complement($color)  //=> color

// or

complement($color)  //=> color
```

<p>Returns the RGB <a target="_blank" href="https://en.wikipedia.org/wiki/Complementary_colors">complement</a> of <code>$color</code>.</p>
<p>This is identical to <a href="#adjust"><code>color.adjust($color, $hue: 180deg)</code></a>.</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> // Hue 222deg becomes 42deg.
> @debug color.complement(#6b717f)  //=> #7f796b
>
> // Hue 164deg becomes 344deg.
> @debug color.complement(#d2e1dd)  //=> #e1d2d6
>
> // Hue 210deg becomes 30deg.
> @debug color.complement(#036)  //=> #663300
> ```

<h3>Darken</h3>

```sass
darken($color, $amount)  //=> color
```

<p>Makes <code>$color</code> darker.</p>
<p>The <code>$amount</code> must be a number between 0% and 100% (inclusive). Decreases the HSL lightness of <code>$color</code> by that amount.</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> // Lightness 92% becomes 72%.
> @debug darken(#b37399, 20%)  //=> #7c4465
>
> // Lightness 85% becomes 45%.
> @debug darken(#f2ece4, 40%)  //=> #b08b5a
>
> // Lightness 20% becomes 0%.
> @debug darken(#036, 30%)  //=> black
> ```

<h3>Desaturate</h3>

```sass
desaturate($color, $amount)  //=> color
```

<p>Makes <code>$color</code> less saturated.</p>
<p>The <code>$amount</code> must be a number between 0% and 100% (inclusive). Decreases the HSL saturation of <code>$color</code> by that amount.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> // Saturation 100% becomes 80%.
> @debug desaturate(#036, 20%)  //=> #0a335c
>
> // Saturation 35% becomes 15%.
> @debug desaturate(#f2ece4, 20%)  //=> #eeebe8
>
> // Saturation 20% becomes 0%.
> @debug desaturate(#d2e1dd, 30%)  //=> #dadada
> ```

<h3>Grayscale</h3>

```sass
color.grayscale($color)  //=> color

// or

grayscale($color)  //=> color
```

<p>Returns a gray color with the same lightness as <code>$color</code>.</p>
<p>This is identical to <a href="#change"><code>color.change($color, $saturation: 0%)</code></a>.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.grayscale(#6b717f)  //=> #757575
> @debug color.grayscale(#d2e1dd)  //=> #dadada
> @debug color.grayscale(#036)  //=> #333333
> ```

<h3>Green</h3>

```sass
color.green($color)  //=> number

// or

green($color)  //=> number
```

<p>Returns the green channel of <code>$color</code> as a number between 0 and 255.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.green(#e1d7d2)  //=> 215
> @debug color.green(white)  //=> 255
> @debug color.green(black)  //=> 0
> ```

<h3>Hue</h3>

```sass
color.hue($color)  //=> number

// or

hue($color)  //=> number
```

<p>Returns the hue of <code>$color</code> as a number between <code>0deg</code> and <code>360deg</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.hue(#e1d7d2)  //=> 20deg
> @debug color.hue(#f2ece4)  //=> 34.2857142857deg
> @debug color.hue(#dadbdf)  //=> 228deg
> ```

<h3>Hue Whiteness Blackness (HWB)</h3>

```sass
color.hwb($hue $whiteness $blackness)  //=> color

// or

color.hwb($hue $whiteness $blackness / $alpha)  //=> color

// or

color.hwb($hue, $whiteness, $blackness, $alpha: 1)  //=> color
```

<p>Returns a color with the given <a target="_blank" href="https://en.wikipedia.org/wiki/HWB_color_model">hue, whiteness, and blackness</a> and the given alpha channel.</p>
<p>The hue is a number between <code>0deg</code> and <code>360deg</code> (inclusive). The whiteness and blackness are numbers between <code>0%</code> and <code>100%</code> (inclusive). The hue may be <a target="_blank" href="https://sass-lang.com/documentation/values/numbers/#units">unitless</a>, but the whiteness and blackness must have unit %. The alpha channel can be specified as either a unitless number between 0 and 1 (inclusive), or a percentage between <code>0%</code> and <code>100%</code> (inclusive).</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.hwb(210, 0%, 60%)  //=> #036
> @debug color.hwb(34, 89%, 5%)  //=> #f2ece4
> @debug color.hwb(210 0% 60% / 0.5)  //=> rgba(0, 51, 102, 0.5)
> ```

<h3>IE HEX Str</h3>

```sass
color.ie-hex-str($color)  //=> unquoted string

// or

ie-hex-str($color)  //=> unquoted string
```

<p>Returns an unquoted string that represents <code>$color</code> in the <code>#AARRGGBB</code> format expected by Internet Explorer’s <a target="_blank" href="https://learn.microsoft.com/en-us/previous-versions/ms530752(v=vs.85)"><code>-ms-filter</code></a> property.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.ie-hex-str(#b37399)  //=> #FFB37399
> @debug color.ie-hex-str(#808c99)  //=> #FF808C99
> @debug color.ie-hex-str(rgba(242, 236, 228, 0.6))  //=> #99F2ECE4
> ```

<h3>Invert</h3>

```sass
color.invert($color, $weight: 100%)  //=> color

// or

invert($color, $weight: 100%)  //=> color
```

<p>Returns the inverse or <a target="_blank" href="https://en.wikipedia.org/wiki/Negative_(photography)">negative</a> of <code>$color</code>.</p>
<p>The <code>$weight</code> must be a number between <code>0%</code> and <code>100%</code> (inclusive). A higher weight means the result will be closer to the negative, and a lower weight means it will be closer to <code>$color</code>. Weight <code>50%</code> will always produce <code>#808080</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.invert(#b37399)  //=> #4c8c66
> @debug color.invert(black)  //=> white
> @debug color.invert(#550e0c, 20%)  //=> #663b3a
> ```

<h3>Lighten</h3>

```sass
lighten($color, $amount)  //=> color
```

<p>Makes <code>$color</code> lighter.</p>
<p>The <code>$amount</code> must be a number between <code>0%</code> and <code>100%</code> (inclusive). Increases the <b>HSL</b> lightness of <code>$color</code> by that amount.</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> // Lightness 46% becomes 66%.
> @debug lighten(#6b717f, 20%)  //=> #a1a5af
>
> // Lightness 20% becomes 80%.
> @debug lighten(#036, 60%)  //=> #99ccff
>
> // Lightness 85% becomes 100%.
> @debug lighten(#e1d7d2, 30%)  //=> white
> ```

<h3>Lightness</h3>

```sass
color.lightness($color)  //=> number

// or

lightness($color)  //=> number
```

<p>Returns the HSL lightness of $color as a number between <code>0%</code> and <code>100%</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.lightness(#e1d7d2)  //=> 85.2941176471%
> @debug color.lightness(#f2ece4)  //=> 92.1568627451%
> @debug color.lightness(#dadbdf)  //=> 86.4705882353%
> ```

<h3>Mix</h3>

```sass
color.mix($color1, $color2, $weight: 50%)  //=> color

// or

mix($color1, $color2, $weight: 50%)  //=> color
```

<p>Returns a color that’s a mixture of <code>$color1</code> and <code>$color2</code>.</p>
<p>Both the <code>$weight</code> and the relative opacity of each color determines how much of each color is in the result. The <code>$weight</code> must be a number between <code>0%</code> and <code>100%</code> (inclusive). A larger weight indicates that more of <code>$color1</code> should be used, and a smaller weight indicates that more of <code>$color2</code> should be used.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.mix(#036, #d2e1dd)  //=> #698aa2
> @debug color.mix(#036, #d2e1dd, 75%)  //=> #355f84
> @debug color.mix(#036, #d2e1dd, 25%)  //=> #9eb6bf
> @debug color.mix(rgba(242, 236, 228, 0.5), #6b717f)  //=> rgba(141, 144, 152, 0.75)
> ```

<h3>Opacify</h3>

```sass
opacify($color, $amount)  //=> color
```

<p>Makes <code>$color</code> more opaque.</p>
<p>The <code>$amount</code> must be a number between <code>0</code> and <code>1</code> (inclusive). Increases the alpha channel of <code>$color</code> by that amount.</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug opacify(rgba(#6b717f, 0.5), 0.2)  //=> rgba(107, 113, 127, 0.7)
> @debug opacify(rgba(#036, 0.7), 0.3)  //=> #036
> ```

<h3>Fade In</h3>

```sass
fade-in($color, $amount)  //=> color
```

<p>Makes <code>$color</code> more opaque.</p>
<p>The <code>$amount</code> must be a number between <code>0</code> and <code>1</code> (inclusive). Increases the alpha channel of <code>$color</code> by that amount.</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug fade-in(rgba(#e1d7d2, 0.5), 0.4)  //=> rgba(225, 215, 210, 0.9)
> ```

<h3>Red</h3>

```sass
color.red($color)  //=> number

// or

red($color)  //=> number
```

<p>Returns the red channel of <code>$color</code> as a number between 0 and 255.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.red(#e1d7d2)  //=> 225
> @debug color.red(white)  //=> 255
> @debug color.red(black)  //=> 0
> ```

<h3>Saturate</h3>

```sass
color.saturate($color, $amount)  //=> color

// or

saturate($color, $amount)  //=> color
```

<p>Makes <code>$color</code> more saturated.</p>
<p>The <code>$amount</code> must be a number between <code>0%</code> and <code>100%</code> (inclusive). Increases the HSL saturation of <code>$color</code> by that amount.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> // Saturation 50% becomes 70%.
> @debug saturate(#c69, 20%)  //=> #e05299
>
> // Saturation 35% becomes 85%.
> @debug desaturate(#f2ece4, 50%)  //=> #ebebeb
>
> // Saturation 80% becomes 100%.
> @debug saturate(#0e4982, 30%)  //=> #004990
> ```

<h3>Saturation</h3>

```sass
color.saturation($color)  //=> number

// or

saturation($color)  //=> number
```

<p>Returns the HSL saturation of <code>$color</code> as a number between <code>0%</code> and <code>100%</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.saturation(#e1d7d2)  //=> 20%
> @debug color.saturation(#f2ece4)  //=> 30%
> @debug color.saturation(#dadbdf)  //=> 7.2463768116%
> ```

<h3>Scale</h3>

```sass
color.scale($color,
  $red: null, $green: null, $blue: null,
  $saturation: null, $lightness: null,
  $whiteness: null, $blackness: null,
  $alpha: null
)  //=> color

// or

scale-color(...)  //=> color
```

<p>Fluidly scales one or more properties of <code>$color</code>.</p>
<p>Each keyword argument must be a number between <code>-100%</code> and <code>100%</code> (inclusive). This indicates how far the corresponding property should be moved from its original position towards the maximum (if the argument is positive) or the minimum (if the argument is negative). This means that, for example, <code>$lightness: 50%</code> will make all colors <code>50%</code> closer to maximum lightness without making them fully white.</p>
<p>It’s an error to specify an RGB property (<code>$red</code>, <code>$green</code>, and/or <code>$blue</code>) at the same time as an HSL property (<code>$saturation</code>, and/or <code>$lightness</code>), or either of those at the same time as an HWB property (<code>$whiteness</code>, and/or <code>$blackness</code>).</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.scale(#6b717f, $red: 15%)  //=> #81717f
> @debug color.scale(#d2e1dd, $lightness: -10%, $saturation: 10%)  //=> #b3d4cb
> @debug color.scale(#998099, $alpha: -40%)  //=> rgba(153, 128, 153, 0.6)
> ```

<h3>Transparentize</h3>

```sass
transparentize($color, $amount)  //=> color
```

<p>Makes <code>$color</code> more transparent.</p>
<p>The <code>$amount</code> must be a number between <code>0</code> and <code>1</code> (inclusive). Decreases the alpha channel of <code>$color</code> by that amount.</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug transparentize(rgba(#6b717f, 0.5), 0.2)  //=> rgba(107, 113, 127, 0.3)
> @debug transparentize(rgba(#036, 0.3), 0.3)  //=> rgba(0, 51, 102, 0)
> ```

<h3>Fade Out</h3>

```sass
fade-out($color, $amount)  //=> color
```

<p>Makes <code>$color</code> more transparent.</p>
<p>The <code>$amount</code> must be a number between <code>0</code> and <code>1</code> (inclusive). Decreases the alpha channel of <code>$color</code> by that amount.</p>
<p></p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> // rgba(#036, 0.3) has alpha 0.3, so when transparentize() subtracts 0.3 it
> // returns a fully transparent color.
> @debug transparentize(rgba(#036, 0.3), 0.3)  //=> rgba(0, 51, 102, 0)
> ```

<h3>Whiteness</h3>

```sass
color.whiteness($color)  //=> number
```

<p>Returns the HWB whiteness of <code>$color</code> as a number between <code>0%</code> and <code>100%</code>.</p>

> **Sass**
>
> ```sass
> @use "sasses/color"
>
> @debug color.whiteness(#e1d7d2)  //=> 82.3529411765%
> @debug color.whiteness(white)  //=> 100%
> @debug color.whiteness(black)  //=> 0%
> ```
