
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

* The first version of the variables (h13-h15 and p13-p15) were obtained from the [published UCR reports](https://www.fbi.gov/how-we-can-help-you/more-fbi-services-and-information/ucr/publications); the second version of the variables will be presented below.
* R output:

```R
> df <- read.csv(file="rr.csv",sep=",",header=T)
> head(df)
         city h13    p13 h14    p14 h15    p15 h13a   p13a
1 albuquerque  37 558165  30 558874  43 559721   37 558165
2     anaheim  11 345320  14 346956  18 349471   11 345320
3   anchorage  14 299455  12 301306  26 301239   14 299455
4   arlington  18 378765  13 382976   8 387565   18 378765
5     atlanta  84 451020  93 454363  94 464710   83 451020
6      aurora  23 343484  11 350948  24 360237   20 343484
  h14a   p14a h15a   p15a
1   30 558874   43 559721
2   14 346956   18 349471
3   12 301306   26 301239
4   13 382976    8 387565
5   93 454363   94 464710
6    9 350948   25 360237
> 
> df$r13 <- (df$h13/df$p13)*100000
> df$r15 <- (df$h15/df$p15)*100000
> df$delta <- df$r15-df$r13
> table(df$delta,exclude=NULL)

   -4.2264944303562   -3.09145577990332   -2.68811715695588 
                  1                   1                   1 
  -2.61169179198061   -2.53940280770674   -2.27595185869848 
                  1                   1                   1 
  -2.02032578975854   -1.56677857332485   -1.51125478314244 
                  1                   1                   1 
  -1.50715229423988   -1.49730314435406   -1.42613963520725 
                  1                   1                   1 
  -1.33108538180323   -1.30760461031011   -1.05477823219939 
                  1                   1                   1 
 -0.948633090260879  -0.942764225746169  -0.921588768430544 
                  1                   1                   1 
 -0.748286832337622  -0.674799228783991  -0.670959677551942 
                  1                   1                   1 
 -0.598233398869121  -0.576017206824496  -0.573037945591837 
                  1                   1                   1 
 -0.481312313727147  -0.435865005102178    -0.4178367275792 
                  1                   1                   1 
 -0.372513809796698  -0.348065068440382  -0.345721726210054 
                  1                   1                   1 
 -0.248398900418235  -0.147174281238943 -0.0945589196443386 
                  1                   1                   1 
-0.0734691854445692 -0.0649646152220726 -0.0338099823705811 
                  1                   1                   1 
 0.0877996685620186   0.126609162789111   0.154849062796409 
                  1                   1                   1 
  0.188454036054615   0.237348126208547   0.305973833443694 
                  1                   1                   1 
  0.318773563805586    0.32582293937407   0.364669207360681 
                  1                   1                   1 
  0.379466144881643   0.391806764279037   0.408294639824376 
                  1                   1                   1 
  0.415001320725991   0.424121713634324   0.545274015340295 
                  1                   1                   1 
  0.569791256379789   0.645114711905089   0.732965676737821 
                  1                   1                   1 
  0.751471567565807   0.772168210487582   0.791850902535721 
                  1                   1                   1 
  0.821310124610802    1.00661867351688    1.05353468472026 
                  1                   1                   1 
   1.27871370365836    1.32853306639213    1.36076339995745 
                  1                   1                   1 
   1.47822621917223    1.60299224469485    1.60321762490958 
                  1                   1                   1 
   1.66487440956126    1.66519864285879    1.67031798167725 
                  1                   1                   1 
   1.75942460365421    1.90874419906274    1.95617311257009 
                  1                   1                   1 
   1.96353191440305    1.96519079457117    2.08969409697631 
                  1                   1                   1 
   2.28077936414219    2.30004248322125    2.39701502161764 
                  1                   1                   1 
    2.8706561749003    2.93027681479006    3.04507882754164 
                  1                   1                   1 
   3.50360192048708    3.72629847992384    3.94677366539968 
                  1                   1                   1 
    3.9558606780171     4.3686891360957    4.74991482727428 
                  1                   1                   1 
   4.94741688718449    5.00564206289317    5.20776343639668 
                  1                   1                   1 
   5.39744506667302    5.43579144757499    6.84045735196462 
                  1                   1                   1 
   7.49622977951065    8.16576828892071    17.9526153397927 
                  1                   1                   1 
    21.619067863058                <NA> 
                  1                   8 
> subset(df,is.na(delta))
            city h13    p13 h14    p14 h15    p15 h13a   p13a
21     cleveland  55 389181  63 388655  NA     NA   58 389181
23      columbus  NA     NA  83 830811  77 847745   78 816364
29        durham  NA     NA  21 249738  34 257911   25 242865
41      honolulu  NA     NA  NA     NA  15 999307   NA     NA
67        newark 112 278246  93 279110  NA     NA  112 278246
78      portland  14 609136  26 615672  NA     NA   14 609136
79       raleigh  12 428993  NA     NA  NA     NA   12 428993
105 winstonsalem  15 235811  13 238082  NA     NA   15 235811
    h14a   p14a h15a   p15a       r13      r15 delta
21    63 388655   78 387921 14.132242       NA    NA
23    85 830811   83 847745        NA  9.08292    NA
29    21 249738   34 257911        NA 13.18284    NA
41     7 994034   15 999307        NA  1.50104    NA
67    94 279110   NA     NA 40.252151       NA    NA
78    26 615672   NA     NA  2.298337       NA    NA
79    NA     NA   NA     NA  2.797248       NA    NA
105   13 238082   10 241631  6.361026       NA    NA
> 
> ######################################################
> # test 1: sign test for p(city increases from 2013-15)
> # 95% ci using Jeffreys confidence interval assuming
> # the missing cases are missing at random (MAR)
> 
> t <- table(df$delta>0,exclude=NULL)
> t

FALSE  TRUE  <NA> 
   36    61     8 
> 
> inc <- t[2]
> dec <- t[1]
> miss <- t[3]
> 
> inc/(inc+dec)
    TRUE 
0.628866 
> qbeta(p=0.025,shape1=inc,shape2=1+dec)
[1] 0.5248197
> qbeta(p=0.975,shape1=1+inc,shape2=dec)
[1] 0.7248168
> 
> ######################################################
> # test 2: test Ho that average change score is
> # equal to zero (two-tailed) assuming the missing 
> # cases are missing at random (MAR)
> 
> mean(df$delta,na.rm=T)
[1] 1.287467
> t.test(df$delta,conf.level=0.95,na.rm=T)

	One Sample t-test

data:  df$delta
t = 3.5781, df = 96, p-value = 0.0005447
alternative hypothesis: true mean is not equal to 0
95 percent confidence interval:
 0.5732277 2.0017068
sample estimates:
mean of x 
 1.287467 

> 
> ######################################################
> # test 3: test Ho that median change score is
> # equal to zero (two-tailed) assuming the missing 
> # cases are missing at random (MAR)
> 
> median(df$delta,na.rm=T)
[1] 0.4150013
> library(DescTools)
> MedianCI(df$delta,conf.level=0.95,method="exact",na.rm=T)
   median    lwr.ci    upr.ci 
0.4150013 0.1548491 1.0066187 
attr(,"conf.level")
[1] 0.9582707
> 
> ######################################################
> # test 4: calculate bounds on p(city increases)
> 
> lb <- inc/(inc+dec+miss)
> lb
     TRUE 
0.5809524 
> ub <- (inc+miss)/(inc+dec+miss)
> ub
     TRUE 
0.6571429 
> 
> # check that the width of the bounds corresponds to
> # the fraction of cities with missing information
> 
> ub-lb
      TRUE 
0.07619048 
> miss/(inc+dec+miss)
      <NA> 
0.07619048 
> 
> # B-corrected confidence interval for lower bound
> 
> qbeta(p=0.0125,shape1=inc,shape2=1+dec+miss)
[1] 0.4669867
> qbeta(p=0.9875,shape1=1+inc,shape2=dec+miss)
[1] 0.6890145
> 
> # B-corrected confidence interval for upper bound
> 
> qbeta(p=0.0125,shape1=inc+miss,shape2=1+dec)
[1] 0.5443668
> qbeta(p=0.9875,shape1=1+inc+miss,shape2=dec)
[1] 0.7584362
> 
> ######################################################
> # test 5: calculate bounds on the median change score
> 
> min(df$delta,na.rm=T)
[1] -4.226494
> max(df$delta,na.rm=T)
[1] 21.61907
> 
> # lower bound of the median
> 
> delta.min <- df$delta
> delta.min[is.na(df$delta)] <- -4.227
> median(delta.min)
[1] 0.3646692
> MedianCI(delta.min,conf.level=0.975,method="exact")
     median      lwr.ci      upr.ci 
 0.36466921 -0.09455892  0.79185090 
attr(,"conf.level")
[1] 0.9812591
> 
> # upper bound of the median
> 
> delta.max <- df$delta
> delta.max[is.na(df$delta)] <- 21.620
> median(delta.max)
[1] 0.6451147
> MedianCI(delta.max,conf.level=0.975,method="exact")
   median    lwr.ci    upr.ci 
0.6451147 0.2373481 1.6029922 
attr(,"conf.level")
[1] 0.9812591
>
```

#### Crime Data Explorer Analysis

* The second version of the key variables (h13a-h15a and p13a-p15a) were obtained from Jacob Kaplan's [website](https://crimedatatool.com), which, itself, is based on data from the [Crime Data Explorer](https://cde.ucr.cjis.gov/LATEST/webapp/#/pages/home).
* R output:

```Rout
> df <- read.csv(file="rr.csv",sep=",",header=T)
> head(df)
         city h13    p13 h14    p14 h15    p15 h13a   p13a
1 albuquerque  37 558165  30 558874  43 559721   37 558165
2     anaheim  11 345320  14 346956  18 349471   11 345320
3   anchorage  14 299455  12 301306  26 301239   14 299455
4   arlington  18 378765  13 382976   8 387565   18 378765
5     atlanta  84 451020  93 454363  94 464710   83 451020
6      aurora  23 343484  11 350948  24 360237   20 343484
  h14a   p14a h15a   p15a
1   30 558874   43 559721
2   14 346956   18 349471
3   12 301306   26 301239
4   13 382976    8 387565
5   93 454363   94 464710
6    9 350948   25 360237
> 
> df$r13 <- (df$h13a/df$p13a)*100000
> df$r15 <- (df$h15a/df$p15a)*100000
> df$delta <- df$r15-df$r13
> table(df$delta,exclude=NULL)

   -4.2264944303562    -3.3242705574909   -3.09145577990332 
                  1                   1                   1 
  -2.68811715695588   -2.61169179198061   -2.51939538217457 
                  1                   1                   1 
  -2.27595185869848   -2.22248458904939   -2.02032578975854 
                  1                   1                   1 
  -1.56677857332485   -1.51125478314244   -1.50715229423988 
                  1                   1                   1 
  -1.42613963520725   -1.30760461031011   -1.16227007659027 
                  1                   1                   1 
  -1.09898032085559   -1.05477823219939  -0.948633090260879 
                  1                   1                   1 
 -0.942764225746169  -0.921588768430544  -0.748286832337622 
                  1                   1                   1 
 -0.674799228783991  -0.670959677551942  -0.598233398869121 
                  1                   1                   1 
 -0.576017206824496  -0.573037945591837  -0.481312313727147 
                  1                   1                   1 
   -0.4178367275792  -0.372513809796698  -0.348065068440382 
                  1                   1                   1 
 -0.345721726210054  -0.316562591499526  -0.248398900418235 
                  1                   1                   1 
 -0.147174281238943 -0.0945589196443386 -0.0734691854445692 
                  1                   1                   1 
-0.0649646152220726   0.126609162789111   0.154849062796409 
                  1                   1                   1 
  0.188454036054615   0.236118534788995   0.237348126208547 
                  1                   1                   1 
  0.305973833443694   0.318773563805586    0.32582293937407 
                  1                   1                   1 
  0.349595610598684   0.364669207360681   0.379466144881643 
                  1                   1                   1 
  0.391806764279037   0.415001320725991   0.424121713634324 
                  1                   1                   1 
  0.539057913224627   0.569791256379789   0.645114711905089 
                  1                   1                   1 
  0.710123616426307   0.732965676737821   0.791850902535721 
                  1                   1                   1 
  0.821310124610802    1.00661867351688    1.05353468472026 
                  1                   1                   1 
   1.11718817329502    1.20586281142349    1.27871370365836 
                  1                   1                   1 
   1.32853306639213    1.36076339995745    1.44890452872166 
                  1                   1                   1 
   1.47822621917223    1.66519864285879    1.67031798167725 
                  1                   1                   1 
   1.82493728257443    1.90874419906274    1.95617311257009 
                  1                   1                   1 
   1.96353191440305    1.96519079457117    1.96879872509338 
                  1                   1                   1 
   1.97067450595113    2.08969409697631    2.28077936414219 
                  1                   1                   1 
   2.33647070951819    2.39701502161764     2.8706561749003 
                  1                   1                   1 
   2.88905753036919    2.93027681479006    3.04507882754164 
                  1                   1                   1 
   3.50360192048708    3.72629847992384    3.94677366539968 
                  1                   1                   1 
    3.9558606780171     4.3686891360957    4.89685480229449 
                  1                   1                   1 
   4.94741688718449    5.00564206289317    5.20409540890596 
                  1                   1                   1 
   5.20776343639668    5.39744506667302     6.4995743507601 
                  1                   1                   1 
    7.0070129815449    7.49622977951065    8.16576828892071 
                  1                   1                   1 
   17.9526153397927     21.619067863058                <NA> 
                  1                   1                   4 
> subset(df,is.na(delta))
       city h13    p13 h14    p14 h15    p15 h13a   p13a h14a
41 honolulu  NA     NA  NA     NA  15 999307   NA     NA    7
67   newark 112 278246  93 279110  NA     NA  112 278246   94
78 portland  14 609136  26 615672  NA     NA   14 609136   26
79  raleigh  12 428993  NA     NA  NA     NA   12 428993   NA
     p14a h15a   p15a       r13     r15 delta
41 994034   15 999307        NA 1.50104    NA
67 279110   NA     NA 40.252151      NA    NA
78 615672   NA     NA  2.298337      NA    NA
79     NA   NA     NA  2.797248      NA    NA
> 
> ######################################################
> # test 1: sign test for p(city increases from 2013-15)
> # 95% ci using Jeffreys confidence interval assuming
> # the missing cases are missing at random (MAR)
> 
> t <- table(df$delta>0,exclude=NULL)
> t

FALSE  TRUE  <NA> 
   37    64     4 
> 
> inc <- t[2]
> dec <- t[1]
> miss <- t[3]
> 
> inc/(inc+dec)
     TRUE 
0.6336634 
> qbeta(p=0.025,shape1=inc,shape2=1+dec)
[1] 0.5319312
> qbeta(p=0.975,shape1=1+inc,shape2=dec)
[1] 0.727335
> 
> 
> ######################################################
> # test 2: test Ho that average change score is
> # equal to zero (two-tailed) assuming the missing 
> # cases are missing at random (MAR)
> 
> mean(df$delta,na.rm=T)
[1] 1.304559
> t.test(df$delta,conf.level=0.95,na.rm=T)

	One Sample t-test

data:  df$delta
t = 3.686, df = 100, p-value = 0.0003702
alternative hypothesis: true mean is not equal to 0
95 percent confidence interval:
 0.6023918 2.0067257
sample estimates:
mean of x 
 1.304559 

> 
> ######################################################
> # test 3: test Ho that median change score is
> # equal to zero (two-tailed) assuming the missing 
> # cases are missing at random (MAR)
> 
> median(df$delta,na.rm=T)
[1] 0.4241217
> library(DescTools)
> MedianCI(df$delta,conf.level=0.95,method="exact",na.rm=T)
   median    lwr.ci    upr.ci 
0.4241217 0.2361185 1.1171882 
attr(,"conf.level")
[1] 0.9539559
> 
> ######################################################
> # test 4: calculate bounds on p(city increases)
> 
> lb <- inc/(inc+dec+miss)
> lb
     TRUE 
0.6095238 
> ub <- (inc+miss)/(inc+dec+miss)
> ub
    TRUE 
0.647619 
> 
> # check that the width of the bounds corresponds to
> # the fraction of cities with missing information
> 
> ub-lb
      TRUE 
0.03809524 
> miss/(inc+dec+miss)
      <NA> 
0.03809524 
> 
> # B-corrected confidence interval for lower bound
> 
> qbeta(p=0.0125,shape1=inc,shape2=1+dec+miss)
[1] 0.495692
> qbeta(p=0.9875,shape1=1+inc,shape2=dec+miss)
[1] 0.7153638
> 
> # B-corrected confidence interval for upper bound
> 
> qbeta(p=0.0125,shape1=inc+miss,shape2=1+dec)
[1] 0.5345457
> qbeta(p=0.9875,shape1=1+inc+miss,shape2=dec)
[1] 0.7499092
> 
> ######################################################
> # test 5: calculate bounds on the median change score
> 
> min(df$delta,na.rm=T)
[1] -4.226494
> max(df$delta,na.rm=T)
[1] 21.61907
> 
> # lower bound of the median
> 
> delta.min <- df$delta
> delta.min[is.na(df$delta)] <- -4.227
> median(delta.min)
[1] 0.3918068
> MedianCI(delta.min,conf.level=0.975,method="exact")
     median      lwr.ci      upr.ci 
 0.39180676 -0.06496462  1.11718817 
attr(,"conf.level")
[1] 0.9812591
> 
> # upper bound of the median
> 
> delta.max <- df$delta
> delta.max[is.na(df$delta)] <- 21.620
> median(delta.max)
[1] 0.5697913
> MedianCI(delta.max,conf.level=0.975,method="exact")
   median    lwr.ci    upr.ci 
0.5697913 0.2361185 1.3607634 
attr(,"conf.level")
[1] 0.9812591
>
```
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
* Yet, a partial identification analysis reveals that the 95% confidence interval around the lower bound estimate includes 0.5.
* In other words, the data are simply not strong enough for us to infer whether θ is greater than 0.5.
* We reach similar conclusions with the median(Δ) statistic; the missing-at-random analysis leads to an inference that the murder rate increased from 2013 to 2015; however, the confidence interval accompanying the lower bound of the partial identification interval includes zero; this leads us to fail to reject Ho that median(Δ) = 0.

---
#### Simulation Evidence

* In this section, we demonstrate that the confidence interval procedures used for constructing the bounds (both on p(increase) and the median of the change scores) provide coverage at or above the nominal rates.

```Rout
> ######################################################
> # simulation 1: demonstrate coverage rate of Bonferroni
> # corrected sign test bounds
> 
> set.seed(202)
> 
> yes <- 30
> no <- 60
> missing <- 10
> N <- yes+no+missing
> N
[1] 100
> 
> plb <- vector()
> pub <- vector()
> beta.lb.lcl <- vector()
> beta.lb.ucl <- vector()
> beta.ub.lcl <- vector()
> beta.ub.ucl <- vector()
> 
> for(i in 1:1e4){
+   S <- rmultinom(n=1,size=N,
+     prob=c(yes/N,no/N,missing/N))
+ 
+   r <- S[1]
+   plb[i] <- r/N
+   pub[i] <- (r+S[3])/N
+ 
+   beta.lb.lcl[i] <- qbeta(p=0.0125,shape1=1/2+r,shape2=1/2+N-r)
+   beta.lb.ucl[i] <- qbeta(p=0.9875,shape1=1/2+r,shape2=1/2+N-r)
+   beta.ub.lcl[i] <- qbeta(p=0.0125,shape1=1/2+r+S[3],shape2=1/2+N-(r+S[3]))
+   beta.ub.ucl[i] <- qbeta(p=0.9875,shape1=1/2+r+S[3],shape2=1/2+N-(r+S[3]))
+ 
+   }
> 
> pop.lb <- yes/N
> pop.lb
[1] 0.3
> pop.ub <- (yes+missing)/N
> pop.ub
[1] 0.4
> 
> flag <- ifelse(beta.lb.lcl<pop.lb & 
+                beta.lb.ucl>pop.lb &
+                beta.ub.lcl<pop.ub & 
+                beta.ub.ucl>pop.ub,1,0)
> mean(flag)
[1] 0.9544
> 
> 
> ######################################################
> # simulation 2: demonstrate coverage rate of Bonferroni
> # corrected median bounds
> 
> library(DescTools)
> set.seed(229)
> 
> x <- rnorm(n=1e5,mean=100,sd=10)
> q <- ifelse(x>110,1,0)
> m <- rbinom(n=1e5,size=1,p=0.4*q+0.1*(1-q))
> 
> median(x)
[1] 100.0282
> median(x[m==1])
[1] 106.2306
> median(x[m==0])
[1] 99.34413
> 
> minval <- min(x[m==0])
> minval
[1] 60.87774
> maxval <- max(x[m==0])
> maxval
[1] 142.6582
> 
> xlb <- x
> xlb[m==1] <- minval
> pop.lb <- median(xlb)
> pop.lb
[1] 97.24182
> 
> xub <- x
> xub[m==1] <- maxval
> pop.ub <- median(xub)
> pop.ub
[1] 101.4621
> 
> mlb <- vector()
> mub <- vector()
> median.lb.lcl <- vector()
> median.lb.ucl <- vector()
> median.ub.lcl <- vector()
> median.ub.ucl <- vector()
> 
> for(i in 1:1e4){
+   s <- sample(1:1e5,size=100,replace=T)
+   xs <- x[s]
+   ms <- m[s]
+   minval <- min(xs[ms==0])
+   maxval <- max(xs[ms==0])
+   xslb <- xs
+   xslb[ms==1] <- minval
+   xsub <- xs
+   xsub[ms==1] <- maxval
+   mlb[i] <- median(xslb)
+   mub[i] <- median(xsub)
+   lbci <- MedianCI(xslb,conf.level=0.975,method="exact")
+   median.lb.lcl[i] <- lbci[2]
+   median.lb.ucl[i] <- lbci[3]
+   ubci <- MedianCI(xsub,conf.level=0.975,method="exact")
+   median.ub.lcl[i] <- ubci[2]
+   median.ub.ucl[i] <- ubci[3]
+   }
> 
> flag <- ifelse(median.lb.lcl<pop.lb & 
+                median.lb.ucl>pop.lb &
+                median.ub.lcl<pop.ub & 
+                median.ub.ucl>pop.ub,1,0)
> mean(flag)
[1] 0.9623
>
```
