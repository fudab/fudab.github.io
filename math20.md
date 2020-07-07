
# Math 20: Probability

## About

> ### probability distributions
> ### python graph gallery
> ### reproducible python code

> ### main data analysis and math tools: 
> * Numpy
> * Pandas
> * Math
> * Scipy

> ### main ploting tools: 
> * Matplotlib
> * Seaborn
> * Plotly

Original code and data are in the [Github Repository](https://github.com/fudab/Math-20). Both the web page and the code will be updated irregularly.

## Slides 0629

* ### How Much Does a Hershey Kiss Weight?
```python
figure_hershey_dist(n, fsize, fs)
```
<table align = "center">
<thead>
  <tr>
    <th><img width="475" src="./math20/figures/hershey_distribution_1k.png" ></th>
    <th><img width="475" src="./math20/figures/hershey_distribution_10k.png" ></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td align = "center"><img width="475" src="./math20/figures/hershey_distribution_100k.png" ></td>
    <td align = "center"><img width="475" src="./math20/figures/hershey_distribution_1m.png" ></td>
  </tr>
</tbody>
</table>

## Slides 0701

* ### US States 
```python
us_map_html(dict_state, target, title = None, country = 'US', cmap = tealrose)
us_map_png(dict_state, target, title = None, country = 'US', cmap = tealrose)
```
<table align="center">
  <tr>
    <th><iframe src="https://fudab.github.io/math20/figures/US_map_population.html" width="450px" height="300px" scrolling="no" frameBorder="0"></iframe></th>
    <th><iframe src="https://fudab.github.io/math20/figures/US_map_area.html" width="450px" height="300px" scrolling="no" frameBorder="0"></iframe></th>
  </tr>
 </table>
  
* ### Histograms of Discrete Probability Distributions

>   * #### fundamental distributions
```python
figure_discrete_hist(job = 'coin', fsize = (8, 6), fs = 20)
figure_discrete_hist(job = 'dice', fsize = (8, 6), fs = 20)
figure_discrete_hist(job = 'bino', fsize = (8, 6), fs = 20)
figure_discrete_hist(job = 'poisson', fsize = (8, 6), fs = 20)
```
  
<table align = "center">
<thead>
  <tr>
    <th><img width="475" src="./math20/figures/hist_coin.png" ></th>
    <th><img width="475" src="./math20/figures/hist_dice.png" ></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td align = "center"><img width="475" src="./math20/figures/hist_bino.png" ></td>
    <td align = "center"><img width="475" src="./math20/figures/hist_poisson.png" ></td>
  </tr>
</tbody>
</table>

>   * #### refinement of $d\omega$
```python
figure_discrete_hist(job = 'bino_1', fsize = (8, 6), fs = 20)
figure_discrete_hist(job = 'bino_2', fsize = (8, 6), fs = 20)
figure_discrete_hist(job = 'bino_5', fsize = (8, 6), fs = 20)
figure_discrete_hist(job = 'bino_10', fsize = (8, 6), fs = 20)
```
  
<table align = "center">
<thead>
  <tr>
    <th><img width="475" src="./math20/figures/hist_bino_1.png" ></th>
    <th><img width="475" src="./math20/figures/hist_bino_2.png" ></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td align = "center"><img width="475" src="./math20/figures/hist_bino_5.png" ></td>
    <td align = "center"><img width="475" src="./math20/figures/hist_bino_10.png" ></td>
  </tr>
</tbody>
</table>  

* ### Riemann Sum of a Function
```python
figure_riemann_sum(job = 'power', fsize = (8, 6), fs = 20)
figure_riemann_sum(job = 'sin', fsize = (8, 6), fs = 20)
```
<table align = "center">
<thead>
  <tr>
    <th><img width="475" src="./math20/figures/riemann_sum_power.png" ></th>
    <th><img width="475" src="./math20/figures/riemann_sum_sin.png" ></th>
  </tr>
</thead>
</table>  

* ### Exponential Distribution: Density Function and Cumulative Distribution Function
```python
figure_exp_dist(job = 'pdf', fsize = (8, 6), fs = 18)
figure_exp_dist(job = 'cdf', fsize = (8, 6), fs = 18)
```
<table align = "center">
<thead>
  <tr>
    <th><img width="475" src="./math20/figures/exp_pdf.png" ></th>
    <th><img width="475" src="./math20/figures/exp_cdf.png" ></th>
  </tr>
</thead>
</table>

## Slides 0706

* ### $n!$ and Stirling's Formula
```python
stirling(n = 10)
figure_stirling(n = 5, fsize = (8, 6), fs = 18)
```
<table align = "center">
<thead>
  <tr>
    <th><img width="475" src="./math20/figures/stirling.png" ></th>
    <th><img width="475" src="./math20/figures/stirling_ratio.png" ></th>
  </tr>
</thead>
</table>


## Progress

The dates are consistent with the class.

- [x] 0629
- [x] 0701
- [x] 0706
- [ ] 0710
