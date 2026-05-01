---
#### Exploring Changes in City-Level Murder Rates During the Ferguson Era: A Partial Identification Analysis

* Historical events: police killings of Michael Brown in August 2014 (Ferguson, MO) and Freddie Gray in April 2015 (Baltimore, MD)
* FBI Director James Comey and the "Ferguson effect": "Far more people are being killed in America’s cities this year than in many years."
* Emphasis of this study: changes in murder rates, comparing 2013 to 2015
  
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
* Hypothesis: If the Ferguson effect envisioned by Director Comey exists, then *p* should be greater than 0.5.

---
#### Dataset/Methods

* Sample: N = 82 American cities with at least 250,000 population in either 2013, 2014, or 2015.
* Number of murders is based on the FBI's Uniform Crime Reporting Program for the years 2013 and 2015.
* Population size is reported for each city's jurisdiction for the years 2013-2015.
* The murder rate is expressed as the number of murders divided by the population size (on a per 100,000 population scale)

| City | 2013 Murders | 2013 Population | 2015 Murders | 2015 Population | 2013 Rate | 2015 Rate | +/- |
|:-----|-------------:|----------------:|-------------:|----------------:|----------:|----------:|----:|
| Albuquerque | 37    | 558,165         | 43           | 559,721         | 6.629     | 7.682     | +   |
| Anaheim     | 11    | 345,320         | 18           | 349,471         | 3.185     | 5.151     | +   |
| Anchorage   | 14    | 299,455         | 26           | 301,239         | 4.675     | 8.631     | +   |
| Arlington   | 18    | 378,765         | 8            | 387,565         | 4.752     | 2.064     | -   |

*
*
*

| City | 2013 Murders | 2013 Population | 2015 Murders | 2015 Population | 2013 Rate | 2015 Rate | +/- |
|:-----|-------------:|----------------:|-------------:|----------------:|----------:|----------:|----:|
| Tulsa          | 60    | 394,498         | 55           | 401,520         | 15.209    | 13.698    | -   | 
| Virginia Beach | 17    | 450,687         | 19           | 452,797         | 3.772     | 4.196     | +   |
| Washington DC  | 103    | 646,449         | 162         | 672,228         | 15.933     | 24.099   | +   |
| Wichita        | 15    | 386,486         | 27           | 389,824         | 3.881     | 6.926     | +   |

* A problem is that for 4 of the 82 cities, it is not possible to tell whether the murder rate increased or decreased:

| City | 2013 Murders | 2013 Population | 2015 Murders | 2015 Population | 2013 Rate | 2015 Rate | +/- |
|:-----|-------------:|----------------:|-------------:|----------------:|----------:|----------:|----:|
| Honolulu       | NA    | NA         | 15           | 999,307         | NA    | 1.501    | ?   | 
| Newark | 112    | 278,246         | NA           | NA         | 40.252     | NA     | ?   |
| Portland  | 14    | 609,136         | NA         | NA         | 2.298     | NA   | ?   |
| Raleigh        | 12    | 428,993         | NA           | NA         | 2.797     | NA     | ?   |

* Analysis objective: develop a valid estimate of *p*.
* 48 cities experienced an increase
* 30 cities experienced a decrease
* 4 cities had missing information
* estimate *p* = p(observed)*p(increase|observed)+p(missing)*p(increase|missing)
* In addition to *p*, we will calculate a 95% confidence interval for *p*.
* Will use the Jeffreys procedure to calculate the confidence interval (i.e., draw simulated *p*'s from a beta distribution with shape parameters 1/2+number of increases and 1/2+number of decreases).

---
#### Missing-At-Random Results

* Recall that *p* = p(observed)*p(increase|observed)+p(missing)*p(increase|missing)
* p(observed) = 78/82
* p(increase|observed) = 48/78
* p(missing) = 4/82
* p(increase|missing) = ?/4
* missing-at-random (mar) estimate = p(observed)*p(increase|observed)+p(missing)*p(increase|observed)
* mar.est = 78/82 x 48/78 + 4/82 x 48/78 = 0.615
* 95% confidence interval around mar.est = [0.505,0.718]
* reject Ho that p = 0.5

---
#### Bounds Analysis

* minimum value of *p* consistent with the data: 78/82 x 48/78 + 4/82 x 0/4 = 0.585
* maximum value of *p* consistent with the data: 78/82 x 48/78 + 4/82 x 4/4 = 0.634
* notice that 0.634-0.585 = 0.049 which is the same as 4/82 (fraction of cases that are missing)
* 95% confidence interval for the lower and upper bounds: LB: [0.462,0.701] and UB: [0.511,0.745]
* with 4 cities missing, out of 82 cities, the dominant sign of change (p < 0.5 or p > 0.5) is not identified.

---
#### Conclusions

* Murder is among the best measured crimes in the United States.
* Yet, our measures of murder are not without problems.
* One issue is that our principal law enforcement-based measure of murder (the UCR) is based on voluntary participation by agencies.
* Each year, some agencies across the United States are not represented in the nation's crime statistics.
* When we compare crime statistics in different years, the problem is compounded.
* One solution to this problem is to assume that the patterns among the observed agencies are replicated among the missing agencies.
* We call this the missing-at-random (MAR) assumption.
* Advantage of MAR: we can get a point estimate with a confidence interval.
* Disadvantage of MAR: we can't test the assumption.
* Consequence of relying on it: we understate the uncertainty of our analysis.
* A standard MAR analysis would lead us to reject the hypothesis that *p* = 0.5 (a city drawn at random is equally likely to have experienced an increase or a decrease in its murder rate from 2013 to 2015).
* A partial identification analysis leads us to the conclusion that our sample *p* must be somewhere between 0.585 and 0.634.
* The confidence interval around the lower bound estimate of 0.585 is [0.462,0.701]; since this confidence interval includes 0.5, we now fail to reject the hypothesis that *p* = 0.5.
* The data are simply not strong enough to tell us whether *p* is actually greater than 0.5.
