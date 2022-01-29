A series of templates for [Quarto](https://quarto.org/) to convert a single Markdown input into beautiful and simple Word, HTML, and PDF outputs. As using these templates breaks some useful Quarto built-in functionality, also included is a [Pandoc lua filter](https://pandoc.org/lua-filters.html) to make use of some formatting shortcodes, and add some other useful features.

For an example of the HTML output of this workflow, see [https://jmablog.github.io/jamovi-worksheets/](https://jmablog.github.io/jamovi-worksheets/)

## Features

**Pop-out boxes:** Use Pandoc's fenced divs feature to create coloured breakout boxes:

```
::: Aside

Contents here.

:::

```

The current options are `Aside` (yellow), `Questions` (grey), `Tip` (blue), `Success` (green), and `Warning` (red). Check the example outputs to see them in action.

**LaTeX shortcuts:** Use `\wordtoc` to insert a Word table of contents, as this won't be automatically generated when use `toc` options in Pandoc, and `\newpage` for a manual page break.

**Auto-link questions and answers:** Use Pandoc's bracketed spans feature to create linked questions and answers using Q<number> and A<number>:

```

[Q1]{}. The number of this question will be auto-linked to A1 wherever it appears on the page.

...

[A1]{}. This answer is auto-linked to Q1 above.

```

**References:** Store your bibliography using biblatex in `_bib/references.bib`. Create citations in text with [Pandoc's citation format](https://pandoc.org/MANUAL.html#citation-syntax), e.g. `[@Adams2020]`. A full reference list will be automatically placed at the end of the output document, or can be placed anywhere using a [fenced div](https://pandoc.org/MANUAL.html#extension-fenced_divs) with the id `#refs`.

```

:::{#refs}
:::

```

## Usage

- Install [Quarto](https://quarto.org/docs/getting-started/installation.html). Some additional dependencies may be required, for example, a [TeX installation](https://quarto.org/docs/getting-started/installation.html#tex) if you don't have one already, or Python/R if you intend to use them in your materials - see the Quarto installation page for full details. You might also want to grab [Open Sans](https://www.opensans.com/) for the PDF font, or else change it to one you already have in `_quarto.yml`.
- Clone or download this repo to your local machine.
- Write your materials as required - either as plain Markdown files (`.md`) or using Quarto's own file type (`.qmd`). These can be in the base project directory, or stored in sub-folders to more conveniently keep related material together (e.g. image files to be included), in which case the directory structure used will be echoed in the output directory.
- From a terminal at the base project directory, simply run `quarto render`. Your output files should appear in the `_WORKSHEETS` folder.

## Post-render script

If (like me) you want to store your outputs alongside your inputs rather than in their own sub-directory (`_WORKSHEETS`), then a post-render step can be added to move all the output files back into their source directories and then cleanup the output directory. This script is written in Typescript to run in Deno, which is included with Quarto, so no extra dependencies are required. It reads the output directory you are using from the `_quarto.yml` file, cycles through all the files and files in sub-directories (to one level deep) in that output directory, and moves them back alongside their source input files. 

In `_quarto.yml`, simply uncomment the line `post-render: _resources/scripts/return-to-source.ts` to use this script.

## Customisation

The `_quarto.yml` file contains most of the configuration options for these worksheet - in particular, a lot of the PDF output formatting such as fonts (by default I used [Open Sans](https://www.opensans.com/)) or page margins. These are all either [Quarto project options](https://quarto.org/docs/reference/projects/core.html) or [Pandoc options](https://pandoc.org/MANUAL.html#options) - add or change these as desired.

For further customisation, you can simply make changes to the templates themselves in `_resources/templates`. They are named for each output format. If you know CSS / LaTeX / Word styles, go nuts!

## Credit

The html template used is gently adapted from the [GitHub Pandoc HTML5 template](https://htmlpreview.github.io/?https://github.com/tajmone/pandoc-goodies/blob/master/templates/html5/github/GitHub-Template-Preview.html) from the [pandoc-goodies](https://github.com/tajmone/pandoc-goodies) repository by Tristano Ajmone.

Pandoc lua filters are inspired and adapted from examples given in the Pandoc [lua filters GitHub repo](https://github.com/pandoc/lua-filters).