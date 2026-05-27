
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

* According to Pyrooz et al. (2016:7, Appendix A) there were 105 American cities with at least 200,000 population in the year 2010.
* Among these 105 cities, there were 82 American cities with at least 250,000 population in either 2013, 2014, or 2015.
* Number of murders is based on the FBI's Uniform Crime Reporting Program for the years 2013 and 2015.
* Population size is reported for each city's jurisdiction for the years 2013-2015.
* Data set:

```Rout
               city h13     p13 h14     p14 h15     p15 h13a    p13a h14a    p14a h15a    p15a
1       albuquerque  37  558165  30  558874  43  559721   37  558165   30  558874   43  559721
2           anaheim  11  345320  14  346956  18  349471   11  345320   14  346956   18  349471
3         anchorage  14  299455  12  301306  26  301239   14  299455   12  301306   26  301239
4         arlington  18  378765  13  382976   8  387565   18  378765   13  382976    8  387565
5           atlanta  84  451020  93  454363  94  464710   83  451020   93  454363   94  464710
6            aurora  23  343484  11  350948  24  360237   20  343484    9  350948   25  360237
7            austin  26  859180  32  903924  23  938728   26  859180   32  903924   23  938728
8       bakersfield  24  361859  17  367406  22  373887   24  361859   17  367406   22  373887
9         baltimore 233  622671 211  623513 344  621252  233  622671  211  623513  344  621252
10       batonrouge  49  230212  53  229387  60  228727   49  230212   53  229387   60  228727
11       birmingham  63  212001  52  212115  79  212291   63  212001   52  212115   79  212291
12            boise   3  214330   4  216260   1  218844    3  214330    4  216260    1  218844
13           boston  39  643799  53  654413  38  665258   39  643799   53  654413   38  665258
14          buffalo  47  258789  60  258419  41  258096   47  258789   60  258419   41  258096
15       chandleraz   2  248718   1  252369   1  258875    2  248718    1  252369    1  258875
16        charlotte  59  837638  47  856916  61  877817   59  837638   47  856916   61  877817
17     chesapeakeva   9  230577  10  232489  11  235273    8  230577   10  232489   11  235273
18          chicago 414 2720554 411 2724121 478 2728695  416 2720554  415 2724121  481 2728695
19     chulavistaca   2  255073   7  259894   6  265215    2  255073    7  259894    6  265215
20       cincinnati  70  296491  60  297671  66  298478   70  296491   60  297671   67  298478
21        cleveland  55  389181  63  388655  NA      NA   58  389181   63  388655   78  387921
22  coloradosprings  26  436108  20  444949  25  452410   26  436108   20  444949   22  452410
23         columbus  NA      NA  83  830811  77  847745   78  816364   85  830811   83  847745
24    corpuschristi  18  314523  27  319211  17  324326   18  314523   27  319211   17  324326
25           dallas 143 1255015 116 1272396 136 1301977  143 1255015  116 1272396  136 1301977
26           denver  40  648981  31  665353  53  682418   41  648981   31  665353   53  682418
27        desmoines  11  207391   9  208250  19  210403   11  207391    9  208250   19  210403
28          detroit 316  699889 298  684694 295  673225  316  699889  298  684694  287  673225
29           durham  NA      NA  21  249738  34  257911   25  242865   21  249738   34  257911
30           elpaso  10  679700  21  680273  17  686077   10  679700   21  680273   17  686077
31      fortwaynein  31  254820  12  257172  25  259712   33  254820   12  257172   25  259712
32        fortworth  48  789035  NA      NA  55  829731   49  789035   53  804907   56  829731
33        fremontca   1  224475   1  227575   2  232427    1  224475    1  227575    2  232427
34         fresnoca  40  508876  47  513187  39  520837   40  508876   47  513187   39  520837
35        garlandtx   6  235683   5  236414   8  237593    6  235683    5  236414    8  237593
36        gilbertaz   1  225232   0  235430   2  247324    1  225232    0  235430    2  247324
37       glendaleaz  13  234006  NA      NA  13  240374   13  234006   20  236780   13  240374
38       greensboro  27  279343  23  282203  26  285950   27  279343   23  282203   26  285950
39      hendersonnv   8  268237   3  274121   4  282554    8  268237    3  274121    4  282554
40        hialeahfl  13  234182   6  235446   7  238132   13  234182    6  235446    7  238132
41         honolulu  NA      NA  NA      NA  15  999307   NA      NA    7  994034   15  999307
42          houston 214 2180606 242 2219933 303 2275221  214 2180606  242 2219933  303 2275221
43     indianapolis 129  850220 136  858238 148  863675  129  850220  136  858238  148  863675
44           irvine   2  235830   0  242971   2  258198    2  235830    0  242971    2  258198
45         irvingtx   2  228367   5  231708   9  236465    2  228367    5  231708    9  236465
46     jacksonville  93  845745  96  856021  97  867258   93  845745   96  856021   97  867258
47       jerseycity  20  256886  24  260005  27  265159   20  256886   24  260005   27  265159
48       kansascity  99  465514  78  468417 109  473373   99  465514   79  468417  110  473373
49         laredotx   3  247353  NA      NA   8  256280    3  247353   14  250994    8  256280
50         lasvegas  97 1500455 122 1530899 127 1562134   97 1500455  122 1530899  127 1562134
51      lexingtonky  18  308712  20  311848  15  314077   18  308712   20  311848   15  314077
52        lincolnne   5  267565   7  271208   1  276585    5  267565    7  271208    1  276585
53        longbeach  34  469665  23  471123  36  476318   34  469665   23  471123   36  476318
54       losangeles 251 3878725 260 3906772 282 3962726  251 3878725  260 3906772  282 3962726
55       louisville  48  671120  56  677710  81  680550   48  671120   56  677710   82  680550
56        lubbocktx   5  237875  12  241826  16  247271    5  237875   12  241826   16  247271
57          madison   5  242523   7  245788   7  248833    5  242523    5  245788    6  248833
58          memphis 124  657691 140  654922 135  657936  125  657691  139  654922  138  657936
59             mesa  22  456155  13  462092  16  471034   22  456155   13  462092   16  471034
60            miami  71  418394  81  421996  75  437969   71  418394   81  421996   75  437969
61        milwaukee 104  600805  90  600374 145  600400  104  600805   86  600374  146  600400
62      minneapolis  36  396206  31  404461  47  413479   36  396206   31  404461   47  413479
63          modesto  14  204252  11  205820  25  210794   14  204252   11  205820   25  210794
64        nashville  35  635673  41  647689  72  658029   35  635673   42  647689   79  658029
65       neworleans 156  377022 150  387113 164  393447  156  377022  150  387113  164  393447
66          newyork 335 8396126 333 8473938 352 8550861  335 8396126  333 8473938  352 8550861
67           newark 112  278246  93  279110  NA      NA  112  278246   94  279110   NA      NA
68          norfolk  28  247303  31  247078  28  245400   29  247303   31  247078   28  245400
69    northlasvegas   7  225632  12  229436  14  234386    7  225632   12  229436   14  234386
70          oakland  90  403887  80  409994  85  419481   90  403887   80  409994   85  419481
71     oklahomacity  62  605034  45  617975  73  630621   62  605034   45  617975   73  630621
72            omaha  42  425076  32  438465  48  452252   42  425076   32  438465   48  452252
73          orlando  17  253238  15  259675  32  268438   17  253238   15  259675   32  268438
74     philadelphia 247 1553153 248 1559062 280 1567810  247 1553153  248 1559062  280 1567810
75          phoenix 118 1502139 114 1529852 112 1559744  118 1502139  114 1529852  112 1559744
76       pittsburgh  45  307632  69  307613  57  306870   45  307632   69  307613   57  306870
77          planotx   3  275795   4  277822   4  282968    3  275795    4  277822    4  282968
78         portland  14  609136  26  615672  NA      NA   14  609136   26  615672   NA      NA
79          raleigh  12  428993  NA      NA  NA      NA   12  428993   NA      NA   NA      NA
80             reno  14  232561  15  235055  15  239721   14  232561   15  235055   15  239721
81         richmond  37  212830  41  216747  43  220802   37  212830   43  216747   43  220802
82      riversideca  10  316423  12  319453  10  323064   10  316423   12  319453   10  323064
83        rochester  42  210562  27  210347  33  209922   42  210562   32  210347   33  209922
84       sacramento  34  478182  28  482767  43  489717   34  478182   28  482767   43  489717
85       sanantonio  72 1399725 103 1428465  94 1463586   72 1399725  103 1428465   94 1463586
86    sanbernardino  45  214322  43  214588  44  216477   45  214322   43  214588   44  216477
87         sandiego  39 1349306  32 1368690  37 1400467   39 1349306   32 1368690   37 1400467
88     sanfrancisco  48  833863  45  850294  53  863782   48  833863   45  850294   53  863782
89          sanjose  38  992143  32 1009679  30 1031458   38  992143   32 1009679   30 1031458
90         santaana  13  332848  18  336462  12  337304   13  332848   18  336462   12  337304
91       scottsdale   4  225523  NA      NA   6  233872    4  225523    2  229325    6  233872
92          seattle  19  642814  26  663410  23  683700   18  642814   26  663410   24  683700
93          spokane  11  209524  10  211025  12  212698   11  209524   10  211025   12  212698
94          stlouis 120  318563 159  318574 188  317095  120  318563  159  318574  188  317095
95           stpaul  14  294690  11  297984  16  300721   14  294690   11  297984   16  300721
96     stpetersburg  15  247084  19  250772  14  255821   15  247084   19  250772   14  255821
97         stockton  32  299796  49  299519  49  304890   32  299796   49  299519   49  304890
98            tampa  28  351314  28  357124  34  364383   28  351314   28  357124   34  364383
99           toledo  28  283035  24  281150  24  279552   28  283035   24  281150   24  279552
100          tucson  47  525486  NA      NA  31  529675   47  525486   35  527328   31  529675
101           tulsa  60  394498  46  399556  55  401520   60  394498   46  399556   55  401520
102   virginiabeach  17  450687  17  451102  19  452797   17  450687   17  451102   19  452797
103    washingtondc 103  646449 105  658893 162  672228  103  646449  105  658893  162  672228
104         wichita  15  386486  NA      NA  27  389824   15  386486   21  387493   27  389824
105    winstonsalem  15  235811  13  238082  NA      NA   15  235811   13  238082   10  241631
```

* The murder rate is expressed as the number of murders divided by the population size (on a per 100,000 population scale)
* A problem is that for 4 of the 82 cities, it is not possible to tell whether the murder rate increased or decreased:
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
