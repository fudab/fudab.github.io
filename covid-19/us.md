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
    <th class="tg-baqh"><img height="350" src="./figures_us/US_rose_2020-04-12.png" > </th>
    <th class="tg-baqh"><img height="350" src="./figures_us/US_map.png" ></th>
  </tr>
  <tr>
    <td class="tg-0lax">Figure 1 (a): the state level of reported cases as of April 12, 2020 since the ﬁrst reported case in United States in Jan 21, 2020.</td>
    <td class="tg-0lax">Figure 1 (b): the spacial spread of COVID-19 by April 12, 2020. The number of infected is displayed on a logarithmic scale.</td>
  </tr>
  <tr>
    <td class="tg-baqh" colspan="2"><img height="600" src="./figures_us/US_conf.png" ></td>
  </tr>
  <tr>
    <td class="tg-0lax" colspan="2">Fig: 1 (c): The state level growth of confirmed cases. The curve in a panel repre- sents the number of cumulative infected people in the state and the histogram indicates the number of new infected people everyday. </td>
  </tr>
</table>
</center>
> Figure 1: summary of the COVID-19 information by April 11, 2020. The color code in (a) and (c) corresponds to the partisan voting index (PVI) by each state.




