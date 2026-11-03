# [Skeleton](https://getskeleton.com)
Skeleton is a simple, responsive boilerplate to kickstart any responsive project.

Check out <https://getskeleton.com> for documentation and details.

This fork is a modernization proposal - see [What's changed in this fork](#whats-changed-in-this-fork) below.

## Getting started

There are a couple ways to download Skeleton:
- [Download the zip](https://github.com/dhg/Skeleton/releases/download/2.0.4/Skeleton-2.0.4.zip)
- Clone the repo: `git clone https://github.com/dhg/Skeleton.git` (Note: this is under active development, so if you're looking for stable and safe, use the zipped download)


### What's in the download?

The download includes Skeleton's CSS, Normalize CSS as a reset, a sample favicon, and an index.html as a starting point.

```
Skeleton/
├── index.html
├── css/
│   ├── normalize.min.css
│   └── skeleton.css
└── images/
    └── favicon.ico

```

### Why it's awesome

Skeleton is lightweight and simple. It styles only raw HTML elements (with a few exceptions) and provides a responsive grid. Nothing more.
- Around 400 lines of CSS unminified and with comments
- It's a starting point, not a UI framework
- No compiling or installing...just vanilla CSS


## What's changed in this fork

This fork is a modernization proposal: same philosophy (small, vanilla CSS, no build step, styles raw HTML elements plus a responsive grid), brought up to date with current CSS. **Every class in v2.0.4 keeps working with existing markup** - same `.container`/`.row`/`.column`/`.columns`, same `.one` through `.twelve`, same thirds/halves and `.offset-by-*`, same buttons/utilities, same breakpoints.

- **Design tokens** - every color, spacing value, border radius, font family, the container width, and the grid gutter is now a `:root` custom property in `css/skeleton.css`, instead of being hard-coded throughout the file.
- **Dark mode** - automatic via `prefers-color-scheme`, or forced with `data-theme="dark"`/`"light"` on `<html>`. Only color tokens change; nothing else does.
- **Fluid type** - headings scale continuously with `clamp()` instead of jumping at a breakpoint. The two endpoints are the same mobile/desktop sizes v2.0.4 always used.
- **Cascade layers** - the whole stylesheet lives in `@layer skeleton` (with `normalize.css` pulled in below it, in its own lower-priority layer), so any unlayered CSS on your page overrides a Skeleton default automatically, regardless of selector specificity.
- **CSS Grid** - the grid is rebuilt on `display: grid` instead of floats. The math is identical (verified against the original percentages), so rendered widths don't change; no clearfix is needed internally anymore.
- `bower.json` removed (Bower has been unmaintained for years) and `css/normalize.css` no longer needs its own `<link>` tag - `css/skeleton.css` imports it now.

**The one compatibility note:** grid classes (`.column`/`.columns`, `.offset-by-*`) now need a grid-display ancestor to be sized correctly at ≥550px - in practice `.row`, which is how every documented Skeleton layout already nests columns. A `.columns` element used *without* a `.row` wrapper (not a documented pattern, but technically worked before via floats) will stack full-width instead of sitting beside its siblings.

See it for yourself:
- [`compare.html`](compare.html) renders the same demo markup against the original `css/skeleton-v2.css` and the new `css/skeleton.css` side by side.
- [`index.html`](index.html)'s "What's new" section demonstrates the tokens, the dark mode toggle, and how to override a token from your own page.


## Browser support

- Chrome latest
- Firefox latest
- Opera latest
- Safari latest
- IE latest

The above list is non-exhaustive. Skeleton works perfectly with almost all older versions of the browsers above, though IE certainly has large degradation prior to IE9.


## License

All parts of Skeleton are free to use and abuse under the [open-source MIT license](https://github.com/dhg/Skeleton/blob/master/LICENSE.md).


## Extensions

The following are extensions to Skeleton built by the community. They are not officially supported, but all have been tested and are compatible with v2.0 (exact release noted):
- [Skeleton on LESS](https://github.com/whatsnewsaes/Skeleton-less): Skeleton built with LESS for easier replacement of grid, color, and media queries. (Last update was to match v2.0.1)
- [Skeleton on Sass](https://github.com/whatsnewsaes/Skeleton-Sass): Skeleton built with Sass for easier replacement of grid, color, and media queries. (Last update was to match v2.0.1)

Have an extension you want to see here? Just shoot an email to hi@getskeleton.com with your extension!


## Colophon

Skeleton was built using [Sublime Text 3](https://www.sublimetext.com/3) and designed with [Sketch](https://bohemiancoding.com/sketch). The typeface [Raleway](https://www.google.com/fonts/specimen/Raleway) was created by [Matt McInerney](https://matt.cc/) and [Pablo Impallari](https://www.impallari.com/). Icons in the header of the documentation are all derivative work of icons from [The Noun Project](https://thenounproject.com). [Feather](https://thenounproject.com/term/feather/22073) by Zach VanDeHey, [Pen](https://thenounproject.com/term/pen/21163) (with cap) by Ed Harrison, [Pen](https://thenounproject.com/term/pen/32847) (with clicker) by Matthew Hall, and [Watch](https://thenounproject.com/term/watch/48015) by Julien Deveaux.

(The original colophon credited Google's Prettify library for code highlighting; that project is unmaintained and its code.google.com link is dead. This fork doesn't use a highlighting library - `<pre>`/`<code>` blocks are styled by Skeleton's own CSS.)


## Acknowledgement

Skeleton was created by [Dave Gamache](https://twitter.com/dhg) for a better web.
