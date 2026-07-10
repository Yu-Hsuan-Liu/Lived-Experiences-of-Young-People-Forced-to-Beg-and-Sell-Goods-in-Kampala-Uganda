# Lived Experiences of Young People Forced to Beg and Sell Goods in Kampala, Uganda

Screening code associated with the article:

> Moton, L., Dank, M., Liu, Y. H., & Hughes, A. (2023). An Exploration into the Lived Experiences of Young People Forced to Beg and Sell Goods in Kampala, Uganda. *Journal of Human Trafficking*, 1-19. https://doi.org/10.1080/23322705.2023.2247922

## Overview

The definitions of child sex trafficking, adult sex trafficking, and labor trafficking differ, so identifying possible victims in survey data requires combining several threshold answers rather than relying on a single question. This repository provides an example of using regular expressions in R to screen open-ended and multi-option survey responses and flag respondents who meet those thresholds. All sensitive data have been removed; the script references placeholder file names only.

## How the identifier works

The script (`Human_Trafficking_Population_Identifier_Yu-Hsuan_Liu_03262021.Rmd`) builds a binary `Trafficked` indicator from four decision rules. Each rule pairs a gating question with a follow-up question describing what prevented the respondent from leaving or refusing the work:

1. Not free to leave (Q33 = No) combined with wanting to leave (Q35 = Yes) and a coercion indicator in Q37.
2. Unable to refuse work (Q54 = No) combined with a coercion indicator in Q55.
3. Forced work reported in any Q57 item combined with a coercion indicator in Q58.
4. Forced activity reported in any Q59 item combined with a coercion indicator in Q61.

The coercion indicators are matched with case-insensitive regular expressions covering responses such as physical violence, physical restraint, deprivation, sexual violence, emotional violence, harm to family members, threats of legal action, withholding of identity documents, confiscation of savings, isolation far from home, and induced alcohol or drug use. A respondent who satisfies any of the four rules is coded 1 on `Trafficked`.

## Repository contents

| File | Description |
|---|---|
| `Human_Trafficking_Population_Identifier_Yu-Hsuan_Liu_03262021.Rmd` | R Markdown script implementing the regex-based victim identification rules. |

## Requirements

R with the dplyr and tidyverse packages (stringr supplies `str_detect` and `regex`).

## Usage

Point the `read.csv` call at a survey export whose columns follow the questionnaire numbering used in the script (Q33, Q35, Q37, Q54, Q55, Q57.1_x, Q58, Q59.1_x, Q61), knit or run the chunks, and the script writes a copy of the data with the added `Trafficked` flag.

## License

MIT License. See `LICENSE`.
