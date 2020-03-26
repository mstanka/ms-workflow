# My workflow with Tailwind CSS in Frontend Mentor Challenge

---

## Choose a [Frontend Mentor challenge](https://www.frontendmentor.io/challenges)

- download it, unzip and move it to your frontendmentor folder
- in VS CODE editor open the folder with the challenge
- create new folder **docs** and move inside **index.html** and **images**
- open terminal in VS CODE

`git init` to create a new Git repository

`touch .gitignore` to create a new file **.gitignore** and write inside:

```javascript
.DS_Store
node_modules
```

- read **README** and **style-guide** with the instructions from FrontendMentor

---

### Installation of [Tailwind CSS](https://tailwindcss.com/) for my project

Tailwind CSS is a utility-first CSS framework, highly customizable, low-level.

`npm init -y` to create **package.json**

`npm install tailwindcss postcss-cli autoprefixer`

`npx tailwind init` to create empty **tailwind.config.js**

- create a new file **postcss.config.js** and write inside:

```javascript
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('autoprefixer')
  ]
}
```

- create a new file **src/tailwind.css** and write inside:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- go to **package.json** and replace scripts by:

```json
"scripts": {
  "build": "postcss src/tailwind.css --verbose -o docs/build/tailwind.css",
  "watch": "postcss src/tailwind.css -o docs/build/tailwind.css --watch"
}
```

`npm run build` to create **docs/build/tailwind.css**
`npm run watch` to watch changes

- in **docs/index.html** add link to a style file

```html
<link rel="stylesheet" href="./build/tailwind.css>
```

---

- update **tailwind.config.js** to extend - to customize predefined styles with the project styles

e.g.:

```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        "strong-cyan": "hsl(171, 66%, 44%)",
        "strong-cyan-dark": "hsl(171, 66%, 33%)",
        "light-blue": "hsl(233, 100%, 69%)",
        "light-blue-dark": "hsl(233, 100%, 59%)",
        "dark-grayish-blue": "hsl(210, 10%, 33%)",
        "grayish-blue": "hsl(201, 11%, 66%)"
      },
      fontFamily: {
        sans: ['"Bai Jamjuree"', "sans-serif"]
      },
      screens: {
      '2xl': '1440px'
      }
    },
  },
  variants: {},
  plugins: []
};
```

use `@apply` to group classes and use them on more places
in **src/tailwind.css**
add them before @import "tailwindcss/utilities";

e.g.:

```css
@import "tailwindcss/base";

h2 {
  @apply font-semibold;
  @apply text-3xl;
  @apply text-dark-grayish-blue;
  @apply leading-tight;
}

@import "tailwindcss/components";

.btn {
  @apply py-4;
  @apply px-10;
  @apply rounded-full;
  @apply shadow-md;
  @apply text-gray-100;
  @apply text-base;
  @apply tracking-wide;
  @apply outline-none;
  @apply cursor-pointer;
}

.btn-cyan {
  @apply bg-strong-cyan;
}

.btn-cyan:hover {
  @apply bg-strong-cyan-dark;
}

@import "tailwindcss/utilities";
```

use the classes in **index.html**

e.g.:

```html
<div class="max-w-screen-2xl mx-auto text-lg font-sans text-grayish-blue text-center bg-white">
```

```html
<button class="btn btn-cyan md:px-12">Download for iOS</button>
```

---

Find more in the [Tailwind documentation](https://tailwindcss.com/)

---

### Use PurgeCss to remove unused CSS

- it will minify your final CSS file

`npm install @fullhuman/postcss-purgecss`

- update **postcss.config.js** with

```javascript
require("@fullhuman/postcss-purgecss")({
  content: [
    './docs/index.html'
  ],
  defaultExtractor: content => content.match(/[\w-/:]+(?<!:)/g) || []
})
```

- to limit minification only for production

```javascript
process.env.NODE_ENV === 'production' && require......
```

run `npm run build`

---

### Create a new GitHub repository and deploy on GitHub

push an existing repository from the command line
`git remote add origin https://github.com/mstanka/YOUR_NEW_REPOSITORY.git`
`git push -u origin master`
