# My refence for Sass

```css
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

```css
@mixin flexCenter($direction){
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: $direction;
}

@include flexCenter(column);
```

```css
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
