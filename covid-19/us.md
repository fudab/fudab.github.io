# [Fu Lab](https://fudab.github.io) <img src="https://fudab.github.io/images/Logo.png" align = "right" alt="" width="50">
## [COVID-19](https://fudab.github.io/covid-19.md)

## When and how will the COVID-19 pandemic end in the United States?
### Xingru Chen and Feng Fu
#### `April 11, 2020`
#### `This report provides preliminary results and is work in progress`

### Abstract
> The COVID-19 pandemic has upended everyone’s normal life, health crisis, lockdowns, and economic percussions in an unprecedented pace and scale. We will get over this pandemic but at what prices? Here we estimate the burden of COVID-19 in the United States, peak time, and total number of infections, in coming months.

### Data
> The data we use in our research consist of four parts: the COVID-19 infection information, the census, and the voting information of the United States as well as the migration information in China. We consider the data in a state level where 50 states as well as District of Columbia are treated as individual compartments. The start date is January 21, 2020.

#### Data Source
* United States
  * COVID-19 information: [New York Times COVID-19 Warehouse](https://github.com/nytimes/covid-19-data)
  * census: [United States Census Bureau](https://simple.wikipedia.org/wiki/List_of_U.S._states_by_population)
  * Rural-Urban Continuum Codes: [United States Department of Agriculture](https://www.ers.usda.gov/data-products/rural-urban-continuum-codes/)
  * migration information: [Descartes Labs](https://github.com/descarteslabs/DL-COVID-19)
  * stock market: [Yahoo Finance](https://finance.yahoo.com/)
  * voting information: [Cook Partisan Voting Index](https://en.wikipedia.org/wiki/Cook_Partisan_Voting_Index)
* Mainland China
  * migration information: [Baidu Qianxi](https://qianxi.baidu.com)
  * census: [China Census Bureau](http://www.chamiji.com)
  
#### Data Processing
<center>
 <table class="tg">
  <tr>
    <th class="tg-cly1"><img width="300" src="./figures_us/US_rose_2020-04-12.png" ></th>
    <th class="tg-cly1" rowspan="3"><img width="400" src="./figures_us/US_conf.png" ></th>
  </tr>
  <tr>
    <td class="tg-cly1">(a) The state level of reported cases as of April 12, 2020 since the ﬁrst reported case in United States in Jan 21, 2020.</td>
  </tr>
  <tr>
    <td class="tg-cly1"><img width="300" src="./figures_us/US_map.png" ></td>
  </tr>
  <tr>
    <td class="tg-cly1">(b) The spacial spread of COVID-19 by April 12, 2020. The number of infected is displayed on a logarithmic scale.</td>
    <td class="tg-cly1">(c) The state level growth of confirmed cases. The curve in a panel repre- sents the number of cumulative infected people in the state and the histogram indicates the number of new infected people everyday.</td>
  </tr>
 </table>
</center>

> Figure 1: Summary of the COVID-19 information by April 12, 2020. The color code in (a) and (c) corresponds to the partisan voting index (PVI) by each state.


 <table align="center">
  <tr>
    <th><img width="700" src="./figures_us/China_IF.png" ></th>
  </tr>
  <tr>
    <td>(a) The nationwide internal-flow ratio in China.</td>
  </tr>
  <tr>
    <td><img width="700" src="./figures_us/Hubei_IF.png" ></td>
  </tr>
  <tr>
    <td>(b) The province level internal-flow ratio in Hubei Province.</td>
  </tr>
  <tr>
    <td><img width="700" src="./figures_us/Wuhan_IF.png" ></td>
  </tr>
  <tr>
    <td>(c) The city level inter-flow ratio in Wuhan City.</td>
  </tr>
 </table>



> Figure 2: The internal-flow ratios on three different levels in China. The time period for calculating the first average plateau value is from January 1, 2020 to January 21, 2020 and that for calculating the second value is from February 1, 2020 to February 21, 2020. The percentage in the title of every panel indicates the after-to-before ratio.


### Method

#### SEIR Model
We consider an SEIR model in a population structure for every state. The systems of ODEs describe the dynnamics in continuous time t, that is, days since the outbreak of the disease:

$$\frac{dS_i(t)}{dt} =  -\beta_i(t) S_i(t) \frac{I_i(t)}{N_i};$$
$$\frac{dE_i(t)}{dt} =  \beta_i(t) S_i(t)  \frac{I_i(t)}{N_i} - \sigma_i(t) E_i(t);$$
$$\frac{dI_i(t)}{dt} =  \sigma_i(t) E_i(t) - \gamma_i(t) I_i(t);$$
$$\frac{dR_i(t)}{dt} =  \gamma_i(t) I_i(t).$$
