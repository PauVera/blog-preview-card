# Frontend Mentor - Blog preview card solution

This is my solution to the [Blog preview card challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/blog-preview-card-ckPaj01IcS).  
This challenge was a great opportunity to practice semantic HTML, responsive typography, and CSS architecture decisions in a small but detail-oriented interface. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [AI Collaboration](#ai-collaboration)
- [Author](#author)


## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page

This challenge also encouraged focusing on semantic HTML, visual precision, and responsive typography. I used it as an opportunity to go a bit further and practice fluid type scaling and CSS architecture.

### Screenshot

![Desktop](/design/mi-solucion/blog-card-preview_desktop.png)
![Mobile](/design/mi-solucion/blog-card-preview_mobile.png)
![Mobile w/ hover and focus-visible states](/design/mi-solucion/blog-card-preview_hover-focus-states.png)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Live site in GitHub](https://pauvera.github.io/blog-preview-card/)

## My process

### Built with

- Semantic HTML5 markup
- Mobile-first workflow
- CSS custom properties (design tokens)
- Flexbox
- CSS Grid
- Component-based CSS architecture
- CSS cascade layers (`@layer`)
- Fluid typography with `clamp()`

### What I learned

This challenge helped me reinforce several ideas that go beyond reproducing a design.

One of the most interesting parts was implementing **fluid typography** for the card title.  
The design uses `20px` on mobile and `24px` on desktop, so instead of using a media query, I decided to make the title scale smoothly using `clamp()`.

To do that, I calculated the middle value based on both the desired font sizes and the viewport range:

\[
m = \frac{font_{max} - font_{min}}{viewport_{max} - viewport_{min}}
\]

Then I converted that slope into a `vw` value and built the final expression:

```css
--fs-700: clamp(1.25rem, 1.18rem + 0.36vw, 1.5rem);
```

This allowed the title to scale from 20px to 24px in a controlled way, reaching its maximum value at the target desktop viewport width.

Another architectural decision I found valuable was choosing Flexbox with gap for the card content instead of using a generic vertical flow utility (such as Andy Bell’s lobotomized owl selector).

Originally, I considered a reusable flow utility, but I concluded that:
- a card is a self-contained interface
- its internal layout is stable and intentional
- display: flex communicates layout structure more clearly in this context

```css
.blog-card__content {
  display: flex;
  flex-direction: column;
  gap: var(--sp-150);
}
```

That felt like a more explicit and maintainable decision for this component.

I also spent time thinking about token roles vs responsive behavior, which led me to create a dedicated fixed token for the author name size:

```css
--fs-200: 0.875rem;
```

This kept the typography system coherent while respecting the original design, where the author name remains fixed at 14px across viewport sizes.


### Continued development

Going forward, I want to continue focusing on:
- layout systems and composition patterns
- design systems and token architecture
- accessibility and keyboard interaction states
- CSS architecture and maintainable styling patterns
- building fluid and responsive interfaces with intention

More specifically, I want to keep improving my ability to make architectural decisions based on component intent, rather than simply choosing a technique because it works.

### AI Collaboration

I used ChatGPT as a thinking partner throughout this challenge. Rather than asking it to make decisions for me, I used it to:
- validate architectural ideas
- reason through the clamp() formula
- explore alternative layout approaches
- review CSS structure and semantics
- refine the documentation and English wording of this README

What worked especially well was using AI as a way to think out loud with pushback. In all cases, I wasn’t looking for the AI to decide for me, but to challenge my assumptions and help me compare alternatives.

One thing this process reinforced is that not every different solution is necessarily a better one. The real work is still in developing the judgment to distinguish between a genuinely better architectural decision and a merely different implementation. That judgment still has to come from me.

## Author

- Website - [Pau's Github](https://github.com/PauVera)
- Frontend Mentor - [@PauVera](https://www.frontendmentor.io/profile/PauVera)