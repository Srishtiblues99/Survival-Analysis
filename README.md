# Survival-Analysis in R Programming Language deals with the prediction of events at a specified time. It deals with the occurrence of an interesting event within a specified time and failure of it produces censored observations i.e incomplete observations. 

Survival analysis in R Programming Language
Biological sciences are the most important application of survival analysis in which we can predict the time for organisms eg. when they will multiply to sizes etc.

Methods used to do survival analysis: 
There are two methods that can be used to perform survival analysis in R programming language: 

1)Kaplan-Meier method
2)Cox Proportional hazard model

#Install the required packages
We’ll use two R packages:
1) survival for computing survival analyses
2) survminer for summarizing and visualizing the results of survival analysis
library('survival')
if(!require(devtools)) install.packages("devtools")
devtools::install_github("kassambara/survminer", build_vignettes = FALSE)
library('survminer')
library('tidyr')

#We have example datasets available but analysis can be done on any chosen data
surdata=read.table("C:/Users/shristi/Documents/survival analysis prac data/CGGA.mRNAseq_693_clinical.20200506.txt",sep="\t",header = T,row.names = 1)
print(head(surdata))

#Compute survival curves: survfit(). Computation of the survival probability based on gender. The function survfit() [in survival package] can be used to compute kaplan-Meier survival estimate. 
fit = survfit(Surv(OS,Censor.alive.0.dead.1.) ~ Gender,data = surdata)
fit

#Visualize survival curves. The function ggsurvplot() [in Survminer R package] produces the survival curves for the two groups of subjects.
ggsurvplot(fit, data= surdata)
ggsurvplot(fit, data= surdata, surv.median.line = 'hv')
install.packages("markdown")
library(markdown)
ggsurvplot(fit,data=surdata,surv.median.line = 'hv',pval = T, risk.table = T)
