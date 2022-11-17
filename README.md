# Frontend Mentor - Four card feature section solution

This is a solution to the [Four card feature section challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/four-card-feature-section-weK1eFYK). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size

### Screenshot

![](./images/screenshot.png)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [https://fananibanani.github.io/four-card-feature-section/](https://fananibanani.github.io/four-card-feature-section/)

## My process

### Built with

- Semantic HTML5 markup
- SCSS
- Sass variables
- CSS Grid
- Mobile-first workflow
- Vanilla Javascript

### What I learned

- Learned how to use @import and partials in SCSS. Admittedly only tried this at the very end when my code was about 95% done.
- Learned a lot more about CSS grid than what basic knowledge I had before. I'm especially proud of how I figured out to do the transition from one-column layout (mobile view) to two-by-two (tablet view) and then to the one-two-one layout (desktop view) as shown in the design.
  - I did this by first creating a 4-row column on mobile.
  - Then for tablet view the grid changes to a two-by-two layout, and the grid-auto-flow kicks in, making sure that the content flows horizontally.
  - And for desktop view the first and last cards span the height of 2 rows. Because of that the last card spills over the tablet grid layout, resulting in an implicitly-created column, so a whole new column and row setup was not needed for desktop view. The grid-auto-flow also changes to column so that the layout matches the design.
  - Here is how this looked in my code:

```scss
main {
  display: grid;
  grid-auto-flow: row;
  grid-template-columns: $card-width-s;
  grid-template-rows: repeat(4, $card-height-s);
  gap: 1.6rem;
  margin: 0 auto max(2rem, 4rem) auto;
  max-width: fit-content;
  place-items: center;

  @media screen and (min-width: $tablet) {
    grid-template-columns: repeat(2, $card-width-l);
    grid-template-rows: repeat(2, $card-height-l);
    grid-auto-columns: $card-width-l;
    gap: 2rem;
  }

  @media screen and (min-width: $desktop) {
    grid-auto-flow: column;
  }
}

.card {
  @media screen and (min-width: $desktop) {
    &:first-of-type,
    &:last-of-type {
      grid-row: span 2;
    }
  }
}
```

- Also learned how to incorporate basic Vanilla Javascript into my HTML and how to manipulate CSS with JS. This wasn't part of the original design, but I felt like the original contrast was horribly low, so I wanted to try to make a toggle to show the difference between the original design and a higher-contrast version that actually passes WCAG criteria.

### Continued development

- The little bit of JS I included in this project has definitely made me wanna do more with Vanilla JS to get a hang of manipulating and updating the DOM.
- I hope to learn more about CSS grid usage in the future, since I still don't have a very good grasp of it.
- I would like to figure out how to make similar designs to this one more responsive. I started with a more responsive code, but in the end opted for fixed widths and heights many places because the design would not work otherwise.

### Useful resources

- [CSS-tricks: grid-auto-flow](https://css-tricks.com/almanac/properties/g/grid-auto-flow/) - This helped me to figure out the grid auto flow setting.
- [Sass At-Rules @import](https://sass-lang.com/documentation/at-rules/import) - This is what helped me understand the usage of @import for partials as I wasn't yet very familiar with it.
- [Under-Engineered Toggles Too](https://adrianroselli.com/2019/08/under-engineered-toggles-too.html)
- [How I built a dark mode toggle](https://hidde.blog/dark-light/)
  - These two articles helped me figure out how to make my low/high contrast toggle button.

## Author

- Frontend Mentor - [@fananibanani](https://www.frontendmentor.io/profile/fananibanani)
