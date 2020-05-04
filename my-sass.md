# My refence for Sass

```scss
@import 'abstracts/variables',
        'abstracts/mixin',

        'base/reset',
        'base/typography',
        'base/utilities',

        'layout/header',
        'layout/section-1features',
        'layout/section-2team',
        'layout/section-3sign',
        'layout/footer';
```

- flexbox

```scss
@mixin flexCenter($direction){
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: $direction;
}

```

```scss
@include flexCenter(column);
```

- media queries

```scss
@mixin media-md {
  @media screen and (min-width: 768px) {
    @content;
  }
}
@mixin media-lg {
  @media screen and (min-width: 1024px) {
    @content;
  }
}
```

- set text color

```scss
@function set-text-color($color) {
  @if (lightness($color) > 50) {
    @return #000;
  } else {
    @return #fff;
  }
}
```

```css
color: set-text-color($dark-color);
```
