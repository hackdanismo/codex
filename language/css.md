# CSS
`CSS (Cascading Style Sheet)` is used to style web pages and websites. A `CSS stylesheet` usually has the file extension of `.css`.

## Add a CSS Stylesheet to HTML
Add a stylesheet to a `HTML` document using a `<link>` tag inside of the `<head>` section.

```html
<head>

    <link rel="stylesheet" href="styles/style.css">
</head>
```

## Hero Image
To make an image to be full width in a hero section using `CSS`, the best option is to use: `width: 100%` with `object-fit: cover`, or use a `CSS background image`. This makes the image stretch across the entire screen while maintaining its proportions.

**Important:** The HTML `width` and `height` should reflect the image's actual `intrinsic dimensions`, not its displayed size. For example, an image that is 1920 × 1080 pixels can still display at 100% width and 500px height through `CSS`.

For `SEO`, `accessibility` and `Core Web Vitals`, an HTML `<img>` is generally the better choice for a meaningful hero image. Decorative hero image should use `<img alt="">` or a `CSS` background.

The `object-fit: cover` property fills the entire hero without stretching the image. Some cropping may occur.

```html
<section class="hero">
  <img src="hero.jpg" alt="Mountain landscape at sunrise" width="1920" height="1080" fetchpriority="high">
</section>
```

```css
.hero {
  width: 100%;
  height: 500px;
  overflow: hidden;
}

.hero img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}
```

A full-width background image can be used when we want text or buttons over the image. You don't need HTML `width`, `height`, or `alt` attributes on a background image because the image is defined in `CSS`. 

```html
<section class="hero">
  <h1>Welcome to Our Website</h1>
  <p>Discover something amazing.</p>
</section>
```

```css
.hero {
  width: 100%;
  min-height: 80vh;

  background-image: url("hero.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
```
