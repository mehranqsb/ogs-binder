# OGS Binder guide

The guide uses the TUBAF class, styles, and partner logos copied from
`/home/mehran/Desktop/OGS_Course_2026/Docs`.

With TeX Live and latexmk installed, run from this directory:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=build ogs_binder_guide.tex
cp build/ogs_binder_guide.pdf ogs_binder_guide.pdf
```

The PDF describes the Binder workflow and configuration; it does not claim
that the full benchmark has been executed and validated in Binder.
