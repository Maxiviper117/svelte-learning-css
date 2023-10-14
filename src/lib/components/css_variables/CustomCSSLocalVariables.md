# Youtube: [Using CSS custom properties like this is a waste](https://www.youtube.com/watch?v=_2LwjfYc1x8)

### Channel [KevinPowell](https://www.youtube.com/@KevinPowell)


# Refactoring CSS with Custom Properties

The after CSS refactors the original code by using CSS custom properties (variables) to streamline the styling for different plan types.

## The Problem

In the original CSS, the styling for each plan type is repeated:

```css
.plan--pram::before {
  background-color: var(--clr-yellow-300); 
}

.plan--bike::before {
  background-color: var(--clr-purple-300);
}

.plan--rocket::before {
  background-color: var(--clr-cyan-300);
}
```

This is not very DRY (Don't Repeat Yourself). We want to consolidate the shared styles.

## Introducing Custom Properties

We can use CSS custom properties to define variables for the different plan styles:

```css
.plan {
  --_shadow: var(--shadow, pink);
  --_icon: var(--icon, red);
  --_button-hover: var(--button-hover, var(--clr-text)); 
}
```

The `--_` prefix indicates these are default values that can be overridden.

## Overriding the Defaults 

For each plan type, we override the default custom properties:

```css
.plan--pram {
  --shadow: var(--clr-yellow-300);
  --icon: var(--clr-yellow-400);
  --button-hover: var(--clr-yellow-400);
}
```

And the CSS uses the custom properties:

```css
.plan::before {
  background: var(--_shadow); 
}

.plan__icon {
  fill: var(--_icon);
}

.button:hover {
  background: var(--_button-hover);
} 
```

## Benefits

- More DRY code
- Easier to change shared styles
- Plan types are configurable through custom properties

By refactoring with custom properties, the CSS is more maintainable and extendable.



<table>
<tr>
<th> Good </th>
<th> Bad </th>
</tr>
<tr>
<td style="vertical-align: top; width: 50%">

# CSS Before
```css
  :root {
        /* colors */
        --clr-white: hsl(220, 37%, 100%);
        --clr-surface: hsl(220, 37%, 97%);
        --clr-text: hsl(244, 44%, 14%);

        --clr-yellow-400: hsl(42, 99%, 69%);
        --clr-yellow-300: hsl(47, 100%, 90%);
        --clr-purple-400: hsl(280, 96%, 45%);
        --clr-purple-300: hsl(282, 89%, 90%);
        --clr-cyan-400: hsl(198, 99%, 49%);
        --clr-cyan-300: hsl(240, 100%, 90%);

        /* font families */
        --ff-base: "IBM Plex Sans", sans-serif;
        --ff-accent: "Young Serif", serif;

        /* font weights */
        --fw-regular: 500;
        --fw-bold: 600;
        --fw-black: 700;

        /* font sizes */
        --fs-300: 1rem;
        --fs-400: 1.125rem;
        --fs-500: 1.375rem;
        --fs-600: 1.75rem;
        --fs-700: 2.25rem;
    }

    * {
        margin: 0;
    }

    body {
        background: var(--clr-surface);
        color: var(--clr-text);
        font-family: var(--ff-base);
        font-size: var(--fs-300);
    }

    p,
    ol,
    li {
        max-width: 60ch;
    }

    .text-center {
        text-align: center;
    }

    .text-center > * {
        margin-inline: auto;
    }

    .page-title {
        font-family: var(--ff-accent);
        font-size: var(--fs-700);
        max-width: 25ch;
        margin-block: 4rem 1.5rem;
    }

    .subtitle {
        font-size: var(--fs-400);
    }

    .button {
        color: inherit;
        font-size: var(--fs-300);
        font-weight: var(--fw-bold);
        background: var(--clr-surface);
        padding: 1em 2em;
        border: 0;
        border-radius: 100vw;
        cursor: pointer;
        box-shadow: 0 0.25rem 0 rgb(0 0 0 / 0.08);
    }

    .button:hover,
    .button:focus {
        color: var(--clr-surface);
        background: var(--clr-text);
    }

    .wrapper {
        width: min(100% - 2rem, 55rem);
        margin-inline: auto;
    }

    .even-columns {
        display: grid;
        gap: 3rem;
    }

    @media (min-width: 720px) {
        .even-columns {
            grid-auto-flow: column;
            grid-auto-columns: 1fr;
        }
    }

    .pricing {
        padding: 0;
        margin-block: 3rem;
        list-style: none;
    }

    .plan {
        position: relative;
        display: grid;
        justify-content: start;
        gap: 1rem;
        background: var(--clr-white);
        padding: 2rem;
        border-radius: 0.75rem;
        box-shadow: 0 0 1rem rgb(0 0 0 / 0.122);
    }

    .plan__icon {
        width: 2.5rem;
    }

    .plan__title {
        font-size: var(--fs-500);
        font-weight: var(--fw-bold);
    }

    .plan__price {
        font-size: var(--fs-600);
        font-weight: var(--fw-black);
    }

    .plan__price span {
        font-size: var(--fs-300);
        font-weight: var(--fw-regular);
    }

    .plan > .button:last-child {
        margin-block-start: 2rem;
    }

    .plan::before {
        content: "";
        position: absolute;
        z-index: -1;
        inset: 0;
        translate: -1.25rem -1.25rem;
        border-radius: inherit;
    }

    .plan--pram::before {
        background-color: var(--clr-yellow-300);
    }

    .plan--bike::before {
        background-color: var(--clr-purple-300);
    }

    .plan--rocket::before {
        background-color: var(--clr-cyan-300);
    }

    .plan--pram .card__icon {
        fill: var(--clr-yellow-400);
    }

    .plan--bike .card__icon {
        fill: var(--clr-purple-400);
    }

    .plan--rocket .card__icon {
        fill: var(--clr-cyan-400);
    }
```

</td>
<td style="vertical-align: top; width: 50%">

# CSS After
```css
   :root {
        /* colors */
        --clr-white: hsl(220, 37%, 100%);
        --clr-surface: hsl(220, 37%, 97%);
        --clr-text: hsl(244, 44%, 14%);

        --clr-yellow-400: hsl(42, 99%, 69%);
        --clr-yellow-300: hsl(47, 100%, 90%);
        --clr-purple-400: hsl(280, 96%, 45%);
        --clr-purple-300: hsl(282, 89%, 90%);
        --clr-cyan-400: hsl(198, 99%, 49%);
        --clr-cyan-300: hsl(240, 100%, 90%);

        /* font families */
        --ff-base: "IBM Plex Sans", sans-serif;
        --ff-accent: "Young Serif", serif;

        /* font weights */
        --fw-regular: 500;
        --fw-bold: 600;
        --fw-black: 700;

        /* font sizes */
        --fs-300: 1rem;
        --fs-400: 1.125rem;
        --fs-500: 1.375rem;
        --fs-600: 1.75rem;
        --fs-700: 2.25rem;
    }

    * {
        margin: 0;
    }

    body {
        background: var(--clr-surface);
        color: var(--clr-text);
        font-family: var(--ff-base);
        font-size: var(--fs-300);
    }

    p,
    ol,
    li {
        max-width: 60ch;
    }

    .text-center {
        text-align: center;
    }

    .text-center > * {
        margin-inline: auto;
    }

    .page-title {
        font-family: var(--ff-accent);
        font-size: var(--fs-700);
        max-width: 25ch;
        margin-block: 4rem 1.5rem;
    }

    .subtitle {
        font-size: var(--fs-400);
    }

    .button {
        color: inherit;
        font-size: var(--fs-300);
        font-weight: var(--fw-bold);
        background: var(--clr-surface);
        padding: 1em 2em;
        border: 0;
        border-radius: 100vw;
        cursor: pointer;
        box-shadow: 0 0.25rem 0 rgb(0 0 0 / 0.08);
    }

    .button:hover,
    .button:focus {
        color: var(--clr-surface);
        background: var(--clr-text);
    }

    .wrapper {
        width: min(100% - 2rem, 55rem);
        margin-inline: auto;
    }

    .even-columns {
        display: grid;
        gap: 3rem;
    }

    @media (min-width: 720px) {
        .even-columns {
            grid-auto-flow: column;
            grid-auto-columns: 1fr;
        }
    }

    .pricing {
        padding: 0;
        margin-block: 3rem;
        list-style: none;
    }

    .plan {
        /*
        Custom local variables
        */
        --_shadow: var(--shadow, pink);
        --_icon: var(--icon, red);
        --_button-hover: var(--button-hover, var(--clr-text));

        position: relative;
        display: grid;
        justify-content: start;
        gap: 1rem;
        background: var(--clr-white);
        padding: 2rem;
        border-radius: 0.75rem;
        box-shadow: 0 0 1rem rgb(0 0 0 / 0.122);
    }

    .plan__icon {
        width: 2.5rem;
        fill: var(--_icon);
    }

    .plan__title {
        font-size: var(--fs-500);
        font-weight: var(--fw-bold);
    }

    .plan__price {
        font-size: var(--fs-600);
        font-weight: var(--fw-black);
    }

    .plan__price span {
        font-size: var(--fs-300);
        font-weight: var(--fw-regular);
    }

    .plan > .button:last-child {
        margin-block-start: 2rem;
    }

    .plan::before {
        content: "";
        position: absolute;
        z-index: -1;
        inset: 0;
        translate: -1.25rem -1.25rem;
        border-radius: inherit;
        background: var(--_shadow);
    }

    /* NEW IMPLEMENTATION */
    .plan .button:hover,
    .plan .button:focus {
        background: var(--_button-hover);
    }

    .plan--pram {
        --shadow: var(--clr-yellow-300);
        --icon: var(--clr-yellow-400);
        --button-hover: var(--clr-yellow-400);
    }

    .plan--bike {
        --shadow: var(--clr-purple-300);
        --icon: var(--clr-purple-400);
        --button-hover: var(--clr-purple-400);
    }

    .plan--rocket {
        --shadow: var(--clr-cyan-300);
        --icon: var(--clr-cyan-400);
        --button-hover: var(--clr-cyan-400);
    }

    /* No longer needed */
    /* .plan--pram::before {
        background-color: var(--clr-yellow-300);
    }

    .plan--bike::before {
        background-color: var(--clr-purple-300);
    }

    .plan--rocket::before {
        background-color: var(--clr-cyan-300);
    }

    .plan--pram .card__icon {
        fill: var(--clr-yellow-400);
    }

    .plan--bike .card__icon {
        fill: var(--clr-purple-400);
    }

    .plan--rocket .card__icon {
        fill: var(--clr-cyan-400);
    } */
```



</td>
</tr>
</table>