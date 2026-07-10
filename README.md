# Lived Experiences of Young People Forced to Beg and Sell Goods in Kampala, Uganda

Victim screening code from:

> Moton, L., Dank, M., Liu, Y. H., & Hughes, A. (2023). An Exploration into the Lived Experiences of Young People Forced to Beg and Sell Goods in Kampala, Uganda. *Journal of Human Trafficking*. https://doi.org/10.1080/23322705.2023.2247922

Definitions of child sex trafficking, adult sex trafficking, and labor trafficking each hinge on different threshold answers, so flagging possible victims in survey data takes a combination of questions rather than any single item. The Rmd shows how this was done with regular expressions in R: four decision rules, each pairing a gating question (not free to leave, unable to refuse work, forced work, forced activity) with a follow-up describing the coercion involved (physical violence, restraint, threats against family, withheld identity documents, induced substance use, and so on). A respondent who meets any rule is coded 1 on a `Trafficked` indicator.

All sensitive data have been removed; the script reads a placeholder file name. To reuse it, point the `read.csv` call at a survey export whose columns follow the questionnaire numbering in the script and run the chunks. Requires R with tidyverse.
