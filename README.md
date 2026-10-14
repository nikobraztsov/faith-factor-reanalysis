# Belief vs Practice in the Faith Factor Replication Data

Reanalysis of Rainero, Stolz & Luijkx (2026), *The Faith Factor*.

## The question

The original paper measures researchers' religiosity with a single 0–8
score built from eight items about belief, practice, and self-identification,
then shows that more religious authors are less supportive of secularization.

A single score assumes all eight items measure the same thing. I test that.
I split the score into belief and practice, and ask which of the two drives
the effect on the two outcomes (personal opinion and publication conclusion).

## Headline result

Belief and practice correlate at **r = 0.83**. Separately, both reduce
support for secularization on both outcomes. In the joint model, practice
survives for opinion and belief survives for publication — but a direct
test of coefficient equality gives **p ≈ 0.35** on both outcomes.

The data cannot tell the two axes apart. That is the substantive finding:
the way you choose to measure religiosity shapes what you find, and the
data do not always let you distinguish two ways of measuring the same thing.

## Data

The replication package is public on OSF: <https://osf.io/vcxnk/>.

Download and unpack it into `data/`:

    data/
    ├── factor analysis/
    │   └── factor_analysis.dta
    └── main analysis/
        └── cleaned_df.dta

Data are not committed here. See `.gitignore`.

## Reproducing the analysis

You need R (≥ 4.2) and RStudio. Install dependencies once:

    install.packages(c(
      "haven", "dplyr", "psych", "diptest",
      "sandwich", "car", "marginaleffects", "ggplot2"
    ))

Then open `analysis.Rmd` and knit, or from the console:

    rmarkdown::render("analysis.Rmd", output_dir = "output")

The rendered report lands in `output/analysis.html`.

## Repository layout

    .
    ├── analysis.Rmd      # full analysis, in R Markdown
    ├── README.md
    ├── .gitignore
    ├── data/             # put the OSF files here (gitignored)
    └── output/           # rendered HTML

## Method summary

- **Data**: 949 articles by 703 authors (Faith Factor replication package).
- **Predictors**: belief (mean of 5 items), practice (mean of 2 items),
  composite 0–8 score rescaled to 0–1.
- **Outcomes**: author opinion (binary), publication conclusion (binary).
- **Models**: logistic regression, standard errors clustered by author,
  marginal effects via `marginaleffects`.
- **Robustness**: quantitative-article subsample, author-level opinion,
  linear hypothesis on coefficient equality, VIF check.

## Note on language and translation

The original version of this analysis was written in Russian, as coursework
for the MA in Computational Social Science at the European University at
St. Petersburg (2026).

The English version in this repository is a translation of that original.
Translation was carried out with the assistance of Claude (Anthropic) and
then reviewed and edited by me. Model settings were the defaults of the
chat interface; no temperature value was specified. Code was not changed
during translation — only prose, comments, section headings, and plot
labels.

Any errors introduced in translation are my own.

## Licence

Code: MIT. Text: CC BY 4.0.