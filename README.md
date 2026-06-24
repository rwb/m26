
---
#### Exploring Changes in City-Level Murder Rates During the Ferguson Era: A Partial Identification Analysis

* Historical events: police killings of Michael Brown in August 2014 (Ferguson, MO) and Freddie Gray in April 2015 (Baltimore, MD)
* FBI Director James Comey and the "Ferguson effect": "Far more people are being killed in America’s cities this year than in many years." (October 23, 2015; [CNN Story](https://www.cnn.com/2015/10/26/politics/fbi-comey-crime-police)).
* Emphasis of this study: changes in murder rates at the city level, comparing 2013 to 2015
  
---
#### Prior Literature

* Pyrooz et al. (2016): examined changes in crime rates in large U.S. cities (105 cities with >200k population in 2010; compared 12 months before and after the Brown killing in Ferguson); no evidence of significant change.
* Rosenfeld (2015): distinguishes between 2 different Ferguson effects; studied 56 large American cities; 40 cities increased and 16 cities decreased from 2014-2015; considerable heterogeneity in city-specific trends.
* Rosenfeld and Wallman (2019); national study of the "spike" in murder rates from 2014-15; 53 large American cities studied from 2010-2015; effort to study the effect of arrest rates on murder rates.
* Gaston et al. (2019) studied homicide rates using CDC data from 2014-2016; goal was to determine whether police killings and civil unrest related to police killings and the opioid epidemic drove homicide rates higher in 586 urban American counties (population > 100k); found evidence in support of the Ferguson effect (particularly in the case of Black victim homicides).
* Important themes in the literature: missing data, strong identification assumptions, and ambiguity about the proper independent variable(s) to use.

---
#### Hypothesis

* Ferguson effect was originally described by Director Comey as a national phenomenon.
* A basic analysis could compare the murder rates in large American cities between 2013 (the year before Ferguson) and 2015 (the year after Ferguson).
* Let *p* be the probability that a city drawn at random experienced an increase in its murder rate from 2013 to 2015.
* Let $\Delta_i$ be the 2015 murder rate minus the 2013 murder rate for city *i*.
* Hypothesis 1: *p* > 0.5.
* Hypothesis 2: E(Δ) > 0
  
---
#### Data Overview

* According to Pyrooz et al. (2016:7, Appendix A) there were 105 American cities with at least 200,000 population in the year 2010.
* We can use these same 105 cities.
* Number of murders is based on the FBI's Uniform Crime Reporting Program for the years 2013 and 2015.
* Population size is also based on each city's jurisdiction as reported in the UCR records for the years 2013, 2014, and 2015.

#### UCR Published Volume Analysis

* The first version of the variables (h13-h15 and p13-p15) were obtained from the [published UCR reports](https://www.fbi.gov/how-we-can-help-you/more-fbi-services-and-information/ucr/publications); the second version of the variables (h13a-h15a and p13a-p15a) were obtained from Jacob Kaplan's [website](https://crimedatatool.com), which, itself, is based on data from the [Crime Data Explorer](https://cde.ucr.cjis.gov/LATEST/webapp/#/pages/home).
* Data set:



---
#### Conclusions

* Murder is among the best measured crimes in the United States (and Teddy's point that our tools for studying patterns and trends are more powerful than ever).
* Yet, our measures of murder are not without problems.
* One issue is that our principal law enforcement-based measure of murder (the UCR) is based on voluntary participation by agencies.
* Each year, some agencies across the United States are not represented in the nation's crime statistics.
* When we compare crime statistics in different years, the problem is compounded.
* One solution to this problem is to assume that the patterns among the observed agencies are replicated among the missing agencies.
* We call this the missing-at-random (MAR) assumption.
* Advantage of MAR: we can get a point estimate with a confidence interval.
* Disadvantage of MAR: we can't test the assumption.
* Consequence of relying on it: we understate the uncertainty of our analysis.
* A standard MAR analysis would lead us to reject the hypothesis that θ = 0.5 (a city drawn at random is equally likely to have experienced an increase or a decrease in its murder rate from 2013 to 2015).
* A partial identification analysis leads us to the conclusion that our sample *p* must be somewhere between 0.561 and 0.646.
* The confidence interval around the lower bound estimate of θ = 0.561 is [0.438,0.679]; since this confidence interval includes 0.5, we now fail to reject the hypothesis that θ = 0.5.
* The data are simply not strong enough for us to infer whether θ is greater than 0.5.
