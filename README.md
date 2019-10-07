# rfc-css-import-dynamic
A proposal for CSS dynamic `@import`.

CSS `@import` could be scoped to a given selector so that it would only be downloaded once
the selector matches.

```css
#about-page {
  @import "path/to/about-page/css";
}

.modal.open {
  @import "path/to/modal/css";
}
```

A browser could decide whether/when to prefetch or preload before the selector matches.
Or we could explicitly tell it to do so (but be careful not to interfere
with the media query suffix syntax):

```css
#about-page {
  @import prefetch "path/to/about-page/css";
}

.modal.open {
  @import preload "path/to/modal/css" screen and (max-width: 768px);
}
```

This could lighten the responsbility of modern module bundlers like `webpack`
to need to understand & package CSS just to be able to import it dynamically
along with the JS modules that use it.
We could bring some users back from CSS-in-JS.

Possible alternate syntax:

```css
.modal.open {
  import: "path/to/modal/css";
}
```
