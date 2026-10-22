 Bayesian Inference for COVID-19 Vaccine Efficacy

STAT 342 project, University of Washington.

## Overview
This project uses Bayesian inference to estimate the efficacy of the Pfizer-BioNTech COVID-19 vaccine and to test whether it exceeds the 30% efficacy threshold, starting from a deliberately skeptical prior.

## Data
- 170 confirmed COVID-19 cases in the trial, of which T = 8 occurred in the vaccine group
- No individual-level data. The analysis uses only these summary counts.

## Model
- Data model: T | π ~ Binomial(170, π), where π is the probability that a given case occurred in the vaccine group (assuming equal-sized trial arms)
- Parameter of interest: vaccine efficacy ψ = (1 − 2π) / (1 − π)
- Prior: Beta(43.03, 43.03), chosen with `beta.select()` from the `LearnBayes` package so that P(ψ ≥ 0.3) = 0.05 and P(ψ ≥ 0) = 0.5 (a skeptical prior: only a 5% prior chance that the vaccine meets the threshold)
- Posterior: Beta(51.03, 205.03)

## Methods
- Derived the prior from stated beliefs about efficacy and converted them to the π scale
- Computed posterior median, 95% equal-tailed credible interval, and 95% highest posterior density interval (`HDInterval`)
- Transformed posterior summaries from π to ψ
- Computed the posterior probability that efficacy is at or below 30%
- Implemented in R with `LearnBayes`, `ggplot2`, and `HDInterval`

## Key Findings
| Quantity | Estimate |
|---|---|
| Posterior median of π | 0.1985 |
| 95% credible interval for π | (0.1528, 0.2503) |
| 95% HPD interval for π | (0.1513, 0.2486) |
| Posterior median of efficacy ψ | 0.7523 (about 75%) |
| 95% credible interval for ψ | (0.6661, 0.8196) |
| Posterior P(ψ ≤ 0.3) | about 1.9 × 10⁻¹³ |

- Even under a prior centered on no effect, the posterior puts nearly all of its probability on efficacy well above 30%.
- The plot of the prior and posterior shows the data strongly outweighing the prior.

## Files
- `STAT-342-Final.pdf'`: knitted report
- `STAT 342 Final.Rmd`: R Markdown file

## Author
Zayna Badr, University of Washington
