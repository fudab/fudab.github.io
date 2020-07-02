
# Math 20: Probability

## About

> ### probability distributions
> ### python graph gallery
> ### reproducible python code
> ### 4 main data analysis and math tools: 
> * Numpy
> * Pandas
> * Math
> * Scipy
> ### 3 main ploting tools: 
> * Matplotlib
> * Seaborn
> * Plotly

Original code and data are in the [Github Repository](https://github.com/fudab/Math-20). 

## Progress

- [x] 0629
- [x] 0701
- [ ] 0706

### Slides 0629

* #### How Much Does a Hershey Kiss Weight?
```python
figure_hershey_dist(n, fsize, fs)
```
<table align = "center">
<thead>
  <tr>
    <th><img width="450" src="./math20/figures/hershey_distribution_1k.png" ></th>
    <th><img width="450" src="./math20/figures/hershey_distribution_10k.png" ></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td align = "center"><img width="450" src="./math20/figures/hershey_distribution_100k.png" ></td>
    <td align = "center"><img width="450" src="./math20/figures/hershey_distribution_1m.png" ></td>
  </tr>
</tbody>
</table>

### Slides 0629

* #### US states 
```python
us_map_html(dict_state, target, title = None, country = 'US', cmap = tealrose)
us_map_png(dict_state, target, title = None, country = 'US', cmap = tealrose)
```
* #### Histograms of discrete probability distributions
```python
figure_discrete_hist(job = 'dice', fsize = (8, 6), fs = 20)
```
* #### Riemann sum of a function
```python
figure_riemann_sum(job = 'power', fsize = (8, 6), fs = 20)
```
