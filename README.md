# trantor

A Metropolis-style theme for the [`ltx-talk`](https://ctan.org/pkg/ltx-talk)
presentation class: Libertinus Serif body, Libertinus Sans titles, a slim
progress bar, and tagged PDF/UA output for accessible slides.

![The title slide and an example slide](preview.png)

## Getting started

trantor needs LuaLaTeX, with a recent TeX Live or MacTeX carrying the Libertinus
fonts and `lua-unicode-math` v0.9+.

Copy `trantor.sty` (and a `logo.png` if you want one) next to your document and
compile twice, so the second pass can fill in the table of contents on the
section pages:

```sh
lualatex slides.tex
lualatex slides.tex
```

`slides.tex` is a short [demo deck](slides.pdf) to strip down into your own.

## Customising

- **Accent colour**: the progress bar and the rule under the title. Set it with
  `\trantorset`, from a hex string or from any xcolor expression:
  ```latex
  \trantorset{accent-html = 2A7AE2}
  \trantorset{accent = blue!60!black}
  ```
- **Slide numbers**: the title and divider slides consume no number, so the
  counter reads "content slide k of n". `\trantorset{numbering = all}` counts
  every slide instead.
- **Logo**: a `logo.png` beside your slides appears on the title page, which
  otherwise omits it. Redefine `\titlelogo` for a different file.
- **Maths font**: Euler by default. Change the `\RequirePackage{lum-euler}` line
  in `trantor.sty` for another.
- **Title spacing**: use `\stitle{...}` instead of `\frametitle{...}` on dense
  slides to keep a clear gap below the title.
- **Divider slides**: `\sectionpage` puts the table of contents on a dark slide,
  the current section picked out and the rest dimmed; `\outlinepage` is the same
  with every entry in full white, for an overview after the title page or
  between parts of a long talk; `\standout{...}` puts a single line of text on
  that slide instead.
- **Emphasis**: `\standoutline{...}` centres a line in the title font on the
  current slide.
- **Reference footnote**: `\footline{...}` pins a small citation to the
  bottom-left of the slide, and `\arxiv{1508.05949}` tags a statement with a
  small grey link to the abstract.
- **Other**: `\yes` and `\no` give a check mark and a cross. `\appendix` starts
  the backup slides, which by default overcount past the total.

## Building

- **Draft** (the default): fast, with tagging disabled.
- **Accessible** (PDF/UA-2): swap the `\DocumentMetadata` line at the top of
  `slides.tex` for the tagged block below it, then compile three times. Give
  every figure an `alt={...}` description so it passes PDF/UA. The rest is
  handled by ltx-talk.

## Credits

Design inspired by Matthias Vogelgesang's
[Metropolis](https://github.com/matze/mtheme) beamer theme (CC BY-SA 4.0). This
is an independent reimplementation for `ltx-talk`.

## License

MIT, see [LICENSE](LICENSE). The Libertinus fonts are licensed separately under
the SIL Open Font License.
