---
title: "Example"
modulecode: "JA2022"
subtitle: "An example worksheet"
abstract: |
    Abstract text, indented by four spaces, will appear before the ToCs in all formats.
---

\wordtoc

# First section

Text here. Text. Teeeeeext.

Text with a citation [@Adams2020] here. @Linthorne2001 also says to use inline citations sometimes.

::: Aside

Fenced divs marked with 'Aside' will get a yellow breakout box.

:::

Text.

::: Success

Fenced divs marked with 'Success' will get a green breakout box.

:::

Text.

::: Tip

Fenced divs marked with 'Tip' will get a blue breakout box.

:::

Text.

::: Warning

Fenced divs marked with 'Warning' will get a red breakout box.

:::

Fenced divs marked with 'Questions' will get a grey breakout box, and questions marked with a `[Q1]{}`, `[Q2]{}` etc, get auto linked to their corresponding answer marked with `[A1]{}`, `[A2]{}` etc.

::: Questions

[Q1]{}. My question here?

[Q2]{}. Second question here?

:::

MORE TEXT HERE.

## Second level heading

You can force a newpage anywhere using the LaTeX shortcode `\newpage`.

\newpage

# References

References will be automatically placed at the end of a document (I suggest including a heading for them still), or you can control their placement anywhere in the document using a fenced div with the id `#refs`:

````
:::{#refs}
:::
````

## Example references

::: {#refs}
:::

\newpage

# Answers to questions

Marked with a `Questions` fenced div to match colouring, but the question/answer linking should work outside a fenced div too.

::: Questions

[A1]{}. My answer here.

[A2]{}. Second answer here.

:::
