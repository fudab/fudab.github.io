---
mathjax: true
categories: github jekyll
---

{% include mathjax.html %}

# [Fu Lab](https://fudab.github.io) <img src="https://fudab.github.io/images/Logo.png" align = "right" alt="" width="50">
## [COVID-19](https://fudab.github.io/covid-19)
## When and how will the COVID-19 pandemic end in the United States?
### Xingru Chen and Feng Fu  
 `Last updated: November 22, 2020`
> This report provides preliminary results and is work in progress. More detailed results and figures are in the [Bag End](https://fudab.github.io/covid-19/bag_end_us). Original code and data are in the [Github Repository](https://github.com/fudab/US-COVID-19-Impact-Assesements). Old results with earlier truncation dates for parameter estimation are in the archives (see bottom of the page).


### Abstract
> The COVID-19 pandemic has upended everyone’s normal life, health crisis, lockdowns, and economic percussions in an unprecedented pace and scale. We will get over this pandemic but at what prices? Here we estimate the burden of COVID-19 in the United States, peak time, and total number of infections, in coming months.

### Data
> The data we use in our research consist of four parts: the COVID-19 infection information, the census, and the voting information of the United States as well as the migration information in China. We consider the data in a state level where 50 states as well as District of Columbia are treated as individual compartments. The start date is January 21, 2020.

#### Data Source
* United States
  * COVID-19 information: [New York Times COVID-19 Warehouse](https://github.com/nytimes/covid-19-data)
  * census: [United States Census Bureau](https://simple.wikipedia.org/wiki/List_of_U.S._states_by_population)
  * rural-urban continuum codes: [United States Department of Agriculture](https://www.ers.usda.gov/data-products/rural-urban-continuum-codes/)
  * migration information: [Descartes Labs](https://github.com/descarteslabs/DL-COVID-19)
  * stock market: [Yahoo Finance](https://finance.yahoo.com/)
  * voting information: [Cook Partisan Voting Index](https://en.wikipedia.org/wiki/Cook_Partisan_Voting_Index)
* Mainland China
  * migration information: [Baidu Qianxi](https://qianxi.baidu.com)
  * census: [China Census Bureau](http://www.chamiji.com)
  
#### Data Processing

<table align="center">
  <tr>
    <th><iframe src="https://fudab.github.io/covid-19/figures_us/US_rose.html" width="450px" height="550px" scrolling="no" frameBorder="0"></iframe></th>
    <th><img width="500px" src="./figures_us/US_conf.png" ></th>
  </tr>
  <tr>
    <td>(a) The state level of reported cases.</td>
    <td>(c) The state level growth of confirmed cases since the ﬁrst reported case in United States in Jan 21, 2020.</td>
  </tr>
  <tr>
    <td align="center"><iframe src="https://fudab.github.io/covid-19/figures_us/US_map.html" width="450px" height="300px" scrolling="no" frameBorder="0"></iframe></td>
    <td align="center"><img width="500px" src="./figures_us/US_conf_dead.png" ></td>
  </tr>
  <tr>
    <td>(b) The spatial spread of COVID-19. The number of infected is displayed on a logarithmic scale.</td>
    <td>(d) The national level growth of confirmed cases as well as deaths.</td>
  </tr>
  <tr>
    <td colspan="2">Figure 1: Summary of the COVID-19 information as of November 21, 2020. For (c), the curve in a panel represents the number of cumulative infected people in the state and the histogram indicates the number of new infected people everyday. The color code in (a) and (c) corresponds to the partisan voting index (PVI) by each state.</td>
  </tr>
</table>

<table align="center">
  <tr>
    <th><img width="350" src="./figures_us/China_IF.png" ></th>
    <th><img width="350" src="./figures_us/Hubei_IF.png" ></th>
    <th><img width="350" src="./figures_us/Wuhan_IF.png" ></th>
  </tr>
  <tr>
    <td>(a) The nationwide internal-flow ratio in China.</td>
    <td>(b) The province level internal-flow ratio in Hubei Province.</td>
    <td>(c) The city level inter-flow ratio in Wuhan City.</td>
  </tr>
  <tr>
    <td colspan="3">Figure 2: The internal-flow ratios on three different levels in China. The time period for calculating the first average plateau value is from January 1, 2020 to January 21, 2020 and that for calculating the second value is from February 1, 2020 to February 21, 2020. The percentage in the title of every panel indicates the after-to-before ratio.</td>
  </tr>
</table>

### Method

#### SEIR Model
We consider an SEIR model in a population structure for every state. The systems of ODEs describe the dynnamics in continuous time t, that is, days since the outbreak of the disease:

<div class="math">
 \begin{equation}
  \begin{cases}
  \displaystyle \frac{dS_i(t)}{dt} =  -\beta_i(t) S_i(t) \frac{I_i(t)}{N_i}, \\
  \displaystyle \frac{dE_i(t)}{dt} =  \beta_i(t) S_i(t)  \frac{I_i(t)}{N_i} - \sigma_i(t) E_i(t), \\
  \displaystyle \frac{dI_i(t)}{dt} =  \sigma_i(t) E_i(t) - \gamma_i(t) I_i(t), \\
  \displaystyle \frac{dR_i(t)}{dt} =  \gamma_i(t) I_i(t). \\
\end{cases}
 \end{equation}
</div>

Here, the subscript $i$ refers to the $i$th compartment on the state level (in other words, the $i$th state) and $N_i(t) = S_i(t) + E_i(t) + I_i(t) + R_i(t)$ is the population size of compartment $i$. 

In general, all three parameters can be time dependent, due to containment efforts (social distancing). Since time $t$ is discrete in practice, we treat these parameters as piecewise functions, of which every piece is a constant. To simplify the problem, we pick three important dates as breaking points of the piecewise functions: `March 15` (since when quarantine was executed), `March 29` (2 weeks after March 15 and since when more severe actions were taken), and `May 17` (7 weeks after March 29 and since when states started to reopen business and public places). As a result, the function $\beta_i(t)$ is split into at most four pieces, same for $\sigma_i(t)$ and $\gamma_i(t)$:

<div class="math">
\begin{equation}
  \begin{cases}
  \displaystyle \beta_{i1}, & \text{before and on March 15} \\
  \displaystyle \beta_{i2}, & \text{from March 16 to March 29} \\
  \displaystyle \beta_{i3}, &  \text{from March 30 to May 17} \\
 \displaystyle \beta_{i4}. &  \text{after and on May 18} \\
\end{cases}
\end{equation}
</div>

#### Exponential and Power Growth

Apart from the above compartmental model, we also experiment with two popular curve fitting models: exponential and power growth. For these kind of least square regression methods, we restrict ourselves to the national cases and start the fitting from `March 16` (right after the first breaking point chosen above) to fix the error in the early states of testing in every state and avoid the rapid growth of the exponential function later on.

More concretely, we assume that the general expressions are:
<div class="math">
\begin{equation}
 f(t) = ae^{bt} + c, \qquad f(t) = at^b + c,
\end{equation}
 </div>

### Parameter Estimation

We turncate the date to `September 20`, which is 13 weeks after `May 17`. Old results with earlier truncation dates for parameter estimation are in the archives.

To obtain a satisfactory estimation of the epidemic parameters for the $i$th state, we apply the `dual annealing` algorithm to perform a nonlinear least square fitting of the variable $R_i(t)$ and find the global minimum value of the residual. The table below shows an ordered dictionary of all the parameter objects required.

<table align="center">
  <tr>
    <th>name</th>
    <th>initial value</th>
    <th>lower bound</th>
    <th>upper bound</th>
    <th>expression</th>
  </tr>
  <tr>
    <td align="center">$N_i$</td>
    <td align="center">$n_i$</td>
    <td align="center"></td>
    <td align="center"></td>
    <td align="center"></td>
  </tr>
  <tr>
    <td align="center">$S_i(0)$</td>
    <td align="center"></td>
    <td align="center"></td>
    <td align="center"></td>
    <td align="center">$N_i - E_i(0) - I_i(0) - R_i(0)$</td>
  </tr>
  <tr>
    <td align="center">$E_i(0)$</td>
    <td align="center">50</td>
    <td align="center">0</td>
    <td align="center">1000</td>
    <td align="center"></td>
  </tr>
  <tr>
    <td align="center">$I_i(0)$</td>
    <td align="center">50</td>
    <td align="center">0</td>
    <td align="center">500</td>
    <td align="center"></td>
  </tr>
  <tr>
    <td align="center">$R_i(0)$</td>
    <td align="center">0</td>
    <td align="center">0</td>
    <td align="center">100</td>
    <td align="center"></td>
  </tr>
  <tr>
    <td align="center">$\beta_{ij}$</td>
    <td align="center">0.5</td>
    <td align="center">0.01</td>
    <td align="center">3</td>
    <td align="center"></td>
  </tr>
  <tr>
    <td align="center">$\sigma_{ij}$</td>
    <td align="center">0.5</td>
    <td align="center">0.02</td>
    <td align="center">1</td>
    <td align="center"></td>
  </tr>
  <tr>
    <td align="center">$\gamma_{ij}$</td>
    <td align="center">0.5</td>
    <td align="center">0.02</td>
    <td align="center">1</td>
    <td align="center"></td>
  </tr>
 <tr>
    <td colspan="5">Table 1: Implementation of parameters according to the sampling of the estimates for epidemic parameters. Here, $n_i$ is the population size of state $i$.</td>
  </tr>
</table>

After obtaining the prior estimation of parameters for every province, we can further calculate the covariance matrix $\text{cov}(\hat{x})$ and hence the standard errors. The covariance matrix contains complete information about the uncertainty of parameter estimators. To get $\text{cov}(\hat{x})$, we use a linear approximation method through the Jacobian matrix $F$:

<div class="math">
\begin{equation}
 \text{cov}(\hat{x}) = s^2(F'F)^{-1}, \qquad \text{with}\, F = \left. \frac{\partial f(x)}{\partial x}\right|_{x = \hat{x}}.
\end{equation}
</div>
Here $s^2$ is the unbiased estimation of the variance $\sigma^2$ obtained from the least square residual:
<div class="math">
\begin{equation}
 s^2 = \frac{S_\text{min}(r, \hat{x})}{(n - p)N},
\end{equation}
</div>
with $n$ being the total number of measurements, $p$ the number of estimated parameters, $n - p$ the degrees of freedom, $N$ the population size and $S_\text{min}(r, \hat{x}) = \displaystyle\sum(r - R(\hat{x}))^2$ the minimum value of the objective function (that is, the least square residual).

To get an error bar, we apply the Monte Carlo sampling method to generate a sample set of parameters, feed them into the ODE equations and produce enough outputs where we choose the `0.005` and the `0.995` quantiles as the lower and upper bounds.

<table align="center">
  <tr>
    <th><img width="600" src="./figures_us/0920/US_SEIR_R_0920.png"></th>
  </tr>
  <tr>
    <td>Figure 3: Cumulative incidence of COVID-19 cases in every one of the 50 U.S. states (D.C. is also included) as well as projected increase and peak time based on real data. The error bar is also shown in every panel.</td>
  </tr>
</table>

We can compare the SEIR model with the least square regression methods. 
<table align="center">
  <tr>
    <th align="center"><img width="600" src="./figures_us/0920/US_R_fitting_0920.png"></th>
  </tr>
  <tr>
    <td>Figure 4: All three models: SEIR, exponential growth and power growth. The start date of the fitting is March 16, 2020. Scatters indicate the actual number of infected people and the curves are the corresponding results of least square fitting. The error bar is shown for R. </td>
  </tr>
</table>

### Discussion on Contact Rate

The experience of China has already shown that strict quarantine can reduce the contact rate and hence suppress the epidemic. To perform some predictions with the case in the US, we can consider different compliance levels of social distancing.

#### Discrete Variation

We first work on four discrete threshold values of contact rate reduction: `100% (status quo)`, `50%`, `25%` and `0` (`complete lockdown`).

<table align="center">
  <tr>
    <th><iframe src="https://fudab.github.io/covid-19/figures_us/0920/US_map_status_quo_0920.html" width="450px" height="300px" scrolling="no" frameBorder="0"></iframe></th>
    <th><iframe src="https://fudab.github.io/covid-19/figures_us/0920/US_map_weak_0920.html" width="450px" height="300px" scrolling="no" frameBorder="0"></iframe></th>
  </tr>
  <tr>
    <td>(a) Status quo contact rate as a result of social distancing.</td>
    <td>(b) 50% reduction.</td>
  </tr>
  <tr>
    <td align="center"><iframe src="https://fudab.github.io/covid-19/figures_us/0920/US_map_moderate_0920.html" width="450px" height="300px" scrolling="no" frameBorder="0"></iframe></td>
    <td align="center"><iframe src="https://fudab.github.io/covid-19/figures_us/0920/US_map_strong_0920.html" width="450px" height="300px" scrolling="no" frameBorder="0"></iframe></td>
  </tr>
  <tr>
    <td>(c) 75% reduction.</td>
    <td>(d) zero contract.</td>
  </tr>
 <tr>
    <td align="center"><img width="600" src="./figures_us/0920/US_I_0920.png"></td>
    <td align="center"><img width="600" src="./figures_us/0920/US_R_0920.png"></td>
  </tr>
  <tr>
    <td>(e) When will the inflection points come? </td>
    <td>(f) When will the curves be flattened?</td>
  </tr>
  <tr>
    <td colspan="2">Figure 5: (a) to (d) present the spatiotemporal spread of predicted COVID-19 on December 1 with different scenarios of contact reductions due to control measures instituted in each State and by the federal government. (e) and (f) show the growth patterns of the number of infected people. </td>
  </tr>
 </table>
 
<table align="center">
  <tr>
    <th><img width="600" src="./figures_us/0920/US_transition_0920.png"></th>
  </tr>
  <tr>
    <td>Figure 6: When will the inflection point come? Or it may have arrived for certain states. We consider the distribution of the date on which a state will encounter the peak value of number of new infected.</td>
  </tr>
</table>

A detailed result for every state is given below.

<table align="center">
  <tr>
    <th><img width="800" src="./figures_us/0920/US_SEIR_I_0920.png"></th>
  </tr>
  <tr>
    <td>Figure 7: Flatten the curve under contact rate reductions for different compliance levels of social distancing. In the ﬁgure legend, we show when the outbreak of COVID-19 in each state will peak under different scenarios.</td>
  </tr>
</table>
 
To what extend the contact rate was suppressed in China with three different scales (national, provincial, city) provide even more references to us. We further estimate the number of people infected (dead) under these contact rate reductions.

<table align="center">
  <tr>
    <th><img width="700" src="./figures_us/0920/US_total_reference_0920.png"></th>
  </tr>
  <tr>
    <td>(a) Number of people infected in the end. If we let the outbreaks continue its current trajectory without any effective measures, the total infections can reach around 41 million. With 50% reduction rate, 9 million infection, and with 75% reductions, 8 million people would get infected. Even for the zero contact rate, around 7 million and 700 thousand cases.</td>
  </tr>
  <tr>
    <td align="center"><img width="700" src="./figures_us/0920/US_dead_total_reference_0920.png"></td>
  </tr>
  <tr>
    <td>(b) Number of people dead in the end. If we let the outbreaks continue its current trajectory without any effective measures, the total deaths can reach around 1 million and 100 thousand. With 50% reduction rate, 250 thousand deaths, and with 75% reductions, 230 thousand people would be dead. Even for the zero contact rate, 220 thousand deaths. </td>
  </tr>
  <tr>
    <td align="center">Figure 8: Mitigation effects by the numbers. </td>
  </tr>
</table>

#### Continuous Variation

We can even consider any contact rate measured on a $[0, 1]$ scale. Here, $0$ stands for zero contact while $1$ means statuo quo contact.

<table align="center">
  <tr>
    <th><img width="800" src="./figures_us/0920/US_contact_rate_R_0920.png"></th>
  </tr>
  <tr>
    <td>Figure 9: How far do we need to push the quarantine? It may vary from state to state. The x axis indicates the contact rate and the y axis is the final number of infected.</td>
  </tr>
</table>


### Old Results 

- [x] [April 5, 2020](https://fudab.github.io/covid-19/us_0405)
- [x] [April 12, 2020](https://fudab.github.io/covid-19/us_0412)
- [x] [April 19, 2020](https://fudab.github.io/covid-19/us_0419) 
- [x] [April 26, 2020](https://fudab.github.io/covid-19/us_0426)
- [x] [May 3, 2020](https://fudab.github.io/covid-19/us_0503)
- [x] [May 10, 2020](https://fudab.github.io/covid-19/us_0510)
- [x] [May 17, 2020](https://fudab.github.io/covid-19/us_0517)
- [x] [May 24, 2020](https://fudab.github.io/covid-19/us_0524)
- [x] [May 31, 2020](https://fudab.github.io/covid-19/us_0531)
- [x] [June 7, 2020](https://fudab.github.io/covid-19/us_0607)
- [x] [June 14, 2020](https://fudab.github.io/covid-19/us_0614)
- [x] [June 21, 2020](https://fudab.github.io/covid-19/us_0621)
- [x] [June 28, 2020](https://fudab.github.io/covid-19/us_0628)
- [x] [July 05, 2020](https://fudab.github.io/covid-19/us_0705)
- [x] [July 12, 2020](https://fudab.github.io/covid-19/us_0712)
- [x] [July 19, 2020](https://fudab.github.io/covid-19/us_0719)
- [x] [July 26, 2020](https://fudab.github.io/covid-19/us_0726)
- [x] [August 2, 2020](https://fudab.github.io/covid-19/us_0802)
- [x] [August 9, 2020](https://fudab.github.io/covid-19/us_0809)
- [x] [August 16, 2020](https://fudab.github.io/covid-19/us_0816)
- [x] [August 23, 2020](https://fudab.github.io/covid-19/us_0823)
- [x] [August 30, 2020](https://fudab.github.io/covid-19/us_0830)
- [ ] [September 6, 2020](https://fudab.github.io/covid-19/us_0906)
- [x] [September 13, 2020](https://fudab.github.io/covid-19/us_0913)
- [x] [September 20, 2020](https://fudab.github.io/covid-19/us_0920)
- [ ] [September 27, 2020](https://fudab.github.io/covid-19/us_0927)

