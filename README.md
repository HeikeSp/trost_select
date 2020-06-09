# trost_select

A LASSO model was used to predict drought tolerance from leaf metabolite and transcript data in potato (*Solanum tuberosum*).
Based on that two populations with lines of superior (MPt) or inferior (MPs) tolerance were selected.

## Training data

- **gene expression** data for 42 marker genes measured by qPCR for 31 potato cultivars grown in three field trials, in total 202 samples
- **metabolite** data for 81 marker analytes measured by GC-MS for 31 potato cultivars grown in five field trials, in total 911 samples

## Test data

- **gene expression** data for 42 marker genes measured by qPCR for 195 potato lines grown in two experiments, in total 803 samples
- **metabolite** data for 81 marker analytes measured by GC-MS for 195 potato lines grown in two experiments, in total 806 samples

## Modeling

For the selection of the MAS population MPt and MPs , predictive models were generated with **LASSO** using the glmnet package (Friedman et al., 2010) in R. The cv.glmnet function was used to run 10-fold cross-validation. The ‘λmin + 1SE’-rule was applied to choose the model and variables (spare model with 29 metabolites and 23 transcripts). Missing values in the metabolite (5.5%) and transcript (2.2%) data were estimated by PCA using the Nipals method from the R-package pcaMethods (Stacklies et al., 2007). The training set included 911 samples for metabolite data originating from five independent field experiments and 202 samples for transcript data from three independent field experiments performed in 2011 and 2012 (Sprenger et al., 2018). The resulting models were used to predict the DRYM of 195 lines from metabolite data (806 samples) and transcript data (803 samples). The predicted DRYM values from both models were ranked and averaged to retrieve the 23 most tolerant (MPt) and 22 most sensitive (MPs) lines.