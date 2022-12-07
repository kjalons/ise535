```python
!pip install plotnine
```

    Requirement already satisfied: plotnine in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (0.10.1)
    Requirement already satisfied: matplotlib>=3.5.0 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from plotnine) (3.5.1)
    Requirement already satisfied: statsmodels>=0.13.2 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from plotnine) (0.13.2)
    Requirement already satisfied: patsy>=0.5.1 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from plotnine) (0.5.2)
    Requirement already satisfied: mizani>=0.8.1 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from plotnine) (0.8.1)
    Requirement already satisfied: pandas>=1.3.5 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from plotnine) (1.4.2)
    Requirement already satisfied: numpy>=1.19.0 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from plotnine) (1.21.5)
    Requirement already satisfied: scipy>=1.5.0 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from plotnine) (1.7.3)
    Requirement already satisfied: pyparsing>=2.2.1 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from matplotlib>=3.5.0->plotnine) (3.0.4)
    Requirement already satisfied: fonttools>=4.22.0 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from matplotlib>=3.5.0->plotnine) (4.25.0)
    Requirement already satisfied: python-dateutil>=2.7 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from matplotlib>=3.5.0->plotnine) (2.8.2)
    Requirement already satisfied: kiwisolver>=1.0.1 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from matplotlib>=3.5.0->plotnine) (1.3.2)
    Requirement already satisfied: cycler>=0.10 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from matplotlib>=3.5.0->plotnine) (0.11.0)
    Requirement already satisfied: pillow>=6.2.0 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from matplotlib>=3.5.0->plotnine) (9.0.1)
    Requirement already satisfied: packaging>=20.0 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from matplotlib>=3.5.0->plotnine) (21.3)
    Requirement already satisfied: palettable in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from mizani>=0.8.1->plotnine) (3.3.0)
    Requirement already satisfied: pytz>=2020.1 in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from pandas>=1.3.5->plotnine) (2021.3)
    Requirement already satisfied: six in /Users/kyleealons/opt/anaconda3/lib/python3.9/site-packages (from patsy>=0.5.1->plotnine) (1.16.0)



```python
##download packages
import plotnine as p9
import pandas as pd
import seaborn as sns
```

## Import Dataset


```python
## import and read dataset
honey = pd.read_csv("US_honey.csv")
## drop entries that don't contain data
honey = honey.dropna()
honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Alabama</td>
      <td>16000</td>
      <td>58</td>
      <td>928000</td>
      <td>28000</td>
      <td>62.0</td>
      <td>575000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Arizona</td>
      <td>52000</td>
      <td>79</td>
      <td>4108000</td>
      <td>986000</td>
      <td>68.0</td>
      <td>2793000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Arkansas</td>
      <td>50000</td>
      <td>60</td>
      <td>3000000</td>
      <td>900000</td>
      <td>64.0</td>
      <td>1920000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>California</td>
      <td>420000</td>
      <td>93</td>
      <td>39060000</td>
      <td>4687000</td>
      <td>60.0</td>
      <td>23436000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Colorado</td>
      <td>45000</td>
      <td>60</td>
      <td>2700000</td>
      <td>1404000</td>
      <td>68.0</td>
      <td>1836000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Florida</td>
      <td>230000</td>
      <td>86</td>
      <td>19780000</td>
      <td>1780000</td>
      <td>63.0</td>
      <td>12461000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Georgia</td>
      <td>70000</td>
      <td>62</td>
      <td>4340000</td>
      <td>260000</td>
      <td>69.0</td>
      <td>2995000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Hawaii</td>
      <td>8000</td>
      <td>129</td>
      <td>1032000</td>
      <td>103000</td>
      <td>55.0</td>
      <td>568000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Idaho</td>
      <td>125000</td>
      <td>48</td>
      <td>6000000</td>
      <td>1020000</td>
      <td>65.0</td>
      <td>3900000</td>
      <td>1995</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Illinois</td>
      <td>11000</td>
      <td>74</td>
      <td>814000</td>
      <td>212000</td>
      <td>102.0</td>
      <td>830000</td>
      <td>1995</td>
    </tr>
  </tbody>
</table>
</div>



### Do honeybees produce less honey per colony today?


```python
## calculate the average yield per colony by year
honey['mean.yield'] = honey.groupby('year')['yield_per_colony'].transform('mean')
honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.yield</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Alabama</td>
      <td>16000</td>
      <td>58</td>
      <td>928000</td>
      <td>28000</td>
      <td>62.0</td>
      <td>575000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Arizona</td>
      <td>52000</td>
      <td>79</td>
      <td>4108000</td>
      <td>986000</td>
      <td>68.0</td>
      <td>2793000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Arkansas</td>
      <td>50000</td>
      <td>60</td>
      <td>3000000</td>
      <td>900000</td>
      <td>64.0</td>
      <td>1920000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>California</td>
      <td>420000</td>
      <td>93</td>
      <td>39060000</td>
      <td>4687000</td>
      <td>60.0</td>
      <td>23436000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Colorado</td>
      <td>45000</td>
      <td>60</td>
      <td>2700000</td>
      <td>1404000</td>
      <td>68.0</td>
      <td>1836000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Florida</td>
      <td>230000</td>
      <td>86</td>
      <td>19780000</td>
      <td>1780000</td>
      <td>63.0</td>
      <td>12461000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Georgia</td>
      <td>70000</td>
      <td>62</td>
      <td>4340000</td>
      <td>260000</td>
      <td>69.0</td>
      <td>2995000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Hawaii</td>
      <td>8000</td>
      <td>129</td>
      <td>1032000</td>
      <td>103000</td>
      <td>55.0</td>
      <td>568000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Idaho</td>
      <td>125000</td>
      <td>48</td>
      <td>6000000</td>
      <td>1020000</td>
      <td>65.0</td>
      <td>3900000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Illinois</td>
      <td>11000</td>
      <td>74</td>
      <td>814000</td>
      <td>212000</td>
      <td>102.0</td>
      <td>830000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
    </tr>
  </tbody>
</table>
</div>




```python
## draw plot
from plotnine import ggplot, aes, geom_line

ggplot(honey) + aes(x="year",y='mean.yield') + geom_line()
```


    
![png](output_6_0.png)
    





    <ggplot: (8782265502172)>



##### The yield per colony has decreased drastically as time has gone on. The yield per colony today is less than 20, wen it used to be more than 65. 

### Which states produce the most honey?



```python
### calculate the mean production by state
honey['mean.production.state'] = honey.groupby('state')['production'].transform('mean')
honey = honey.sort_values(by = 'mean.production.state', ascending= False)
honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.production.state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1020</th>
      <td>1020</td>
      <td>NorthDakota</td>
      <td>520000</td>
      <td>65</td>
      <td>6422000</td>
      <td>6422000</td>
      <td>1.43</td>
      <td>48334000</td>
      <td>2019</td>
      <td>51.050000</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>662</th>
      <td>662</td>
      <td>NorthDakota</td>
      <td>510000</td>
      <td>91</td>
      <td>12995000</td>
      <td>12995000</td>
      <td>150.00</td>
      <td>69615000</td>
      <td>2010</td>
      <td>56.275000</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>202</th>
      <td>202</td>
      <td>NorthDakota</td>
      <td>255000</td>
      <td>105</td>
      <td>26775000</td>
      <td>8836000</td>
      <td>59.00</td>
      <td>15797000</td>
      <td>1999</td>
      <td>65.465116</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>820</th>
      <td>820</td>
      <td>NorthDakota</td>
      <td>490000</td>
      <td>86</td>
      <td>9271000</td>
      <td>9271000</td>
      <td>199.00</td>
      <td>83859000</td>
      <td>2014</td>
      <td>57.350000</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>900</th>
      <td>900</td>
      <td>NorthDakota</td>
      <td>485000</td>
      <td>78</td>
      <td>6809000</td>
      <td>6809000</td>
      <td>185.00</td>
      <td>69986000</td>
      <td>2016</td>
      <td>54.075000</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>NorthDakota</td>
      <td>220000</td>
      <td>108</td>
      <td>23760000</td>
      <td>3802000</td>
      <td>63.00</td>
      <td>14969000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>245</th>
      <td>245</td>
      <td>NorthDakota</td>
      <td>290000</td>
      <td>115</td>
      <td>33350000</td>
      <td>13340000</td>
      <td>56.00</td>
      <td>18676000</td>
      <td>2000</td>
      <td>67.534884</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>781</th>
      <td>781</td>
      <td>NorthDakota</td>
      <td>480000</td>
      <td>69</td>
      <td>6955000</td>
      <td>6955000</td>
      <td>204.00</td>
      <td>67565000</td>
      <td>2013</td>
      <td>52.974359</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>159</th>
      <td>159</td>
      <td>NorthDakota</td>
      <td>230000</td>
      <td>128</td>
      <td>29440000</td>
      <td>8832000</td>
      <td>63.00</td>
      <td>18547000</td>
      <td>1998</td>
      <td>69.953488</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>742</th>
      <td>742</td>
      <td>NorthDakota</td>
      <td>480000</td>
      <td>69</td>
      <td>5962000</td>
      <td>5962000</td>
      <td>192.00</td>
      <td>63590000</td>
      <td>2012</td>
      <td>55.175000</td>
      <td>1.902748e+07</td>
    </tr>
  </tbody>
</table>
</div>




```python
## find the states with the highest production
state_production = honey[['state','mean.production.state']]
state_production.head(10)
state_production.drop_duplicates()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>state</th>
      <th>mean.production.state</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1020</th>
      <td>NorthDakota</td>
      <td>1.902748e+07</td>
    </tr>
    <tr>
      <th>878</th>
      <td>California</td>
      <td>1.569911e+07</td>
    </tr>
    <tr>
      <th>544</th>
      <td>SouthDakota</td>
      <td>1.317504e+07</td>
    </tr>
    <tr>
      <th>800</th>
      <td>Florida</td>
      <td>1.040496e+07</td>
    </tr>
    <tr>
      <th>895</th>
      <td>Montana</td>
      <td>7.302704e+06</td>
    </tr>
    <tr>
      <th>892</th>
      <td>Minnesota</td>
      <td>6.540037e+06</td>
    </tr>
    <tr>
      <th>423</th>
      <td>Texas</td>
      <td>4.794111e+06</td>
    </tr>
    <tr>
      <th>772</th>
      <td>Michigan</td>
      <td>3.743074e+06</td>
    </tr>
    <tr>
      <th>793</th>
      <td>Wisconsin</td>
      <td>3.700333e+06</td>
    </tr>
    <tr>
      <th>268</th>
      <td>Idaho</td>
      <td>3.229185e+06</td>
    </tr>
    <tr>
      <th>660</th>
      <td>NewYork</td>
      <td>2.905333e+06</td>
    </tr>
    <tr>
      <th>657</th>
      <td>Nebraska</td>
      <td>2.357593e+06</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Louisiana</td>
      <td>2.243259e+06</td>
    </tr>
    <tr>
      <th>560</th>
      <td>Georgia</td>
      <td>2.126889e+06</td>
    </tr>
    <tr>
      <th>256</th>
      <td>Washington</td>
      <td>1.971778e+06</td>
    </tr>
    <tr>
      <th>515</th>
      <td>Arkansas</td>
      <td>1.920222e+06</td>
    </tr>
    <tr>
      <th>926</th>
      <td>Iowa</td>
      <td>1.800259e+06</td>
    </tr>
    <tr>
      <th>675</th>
      <td>Wyoming</td>
      <td>1.626704e+06</td>
    </tr>
    <tr>
      <th>334</th>
      <td>Oregon</td>
      <td>1.621815e+06</td>
    </tr>
    <tr>
      <th>1036</th>
      <td>Arizona</td>
      <td>1.438667e+06</td>
    </tr>
    <tr>
      <th>999</th>
      <td>Colorado</td>
      <td>1.209630e+06</td>
    </tr>
    <tr>
      <th>703</th>
      <td>Ohio</td>
      <td>8.327778e+05</td>
    </tr>
    <tr>
      <th>823</th>
      <td>Pennsylvania</td>
      <td>7.914815e+05</td>
    </tr>
    <tr>
      <th>893</th>
      <td>Mississippi</td>
      <td>7.864815e+05</td>
    </tr>
    <tr>
      <th>669</th>
      <td>Utah</td>
      <td>7.544074e+05</td>
    </tr>
    <tr>
      <th>108</th>
      <td>Missouri</td>
      <td>6.631111e+05</td>
    </tr>
    <tr>
      <th>802</th>
      <td>Hawaii</td>
      <td>5.711111e+05</td>
    </tr>
    <tr>
      <th>455</th>
      <td>NewMexico</td>
      <td>5.601111e+05</td>
    </tr>
    <tr>
      <th>174</th>
      <td>Alabama</td>
      <td>5.358148e+05</td>
    </tr>
    <tr>
      <th>1007</th>
      <td>Kansas</td>
      <td>5.236296e+05</td>
    </tr>
    <tr>
      <th>617</th>
      <td>Nevada</td>
      <td>4.932667e+05</td>
    </tr>
    <tr>
      <th>884</th>
      <td>Illinois</td>
      <td>3.653333e+05</td>
    </tr>
    <tr>
      <th>805</th>
      <td>Indiana</td>
      <td>3.587407e+05</td>
    </tr>
    <tr>
      <th>330</th>
      <td>NorthCarolina</td>
      <td>3.299630e+05</td>
    </tr>
    <tr>
      <th>211</th>
      <td>Vermont</td>
      <td>2.604444e+05</td>
    </tr>
    <tr>
      <th>977</th>
      <td>NewJersey</td>
      <td>2.560370e+05</td>
    </tr>
    <tr>
      <th>504</th>
      <td>Tennessee</td>
      <td>2.539630e+05</td>
    </tr>
    <tr>
      <th>344</th>
      <td>WestVirginia</td>
      <td>2.374444e+05</td>
    </tr>
    <tr>
      <th>904</th>
      <td>SouthCarolina</td>
      <td>2.352500e+05</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Oklahoma</td>
      <td>2.283333e+05</td>
    </tr>
    <tr>
      <th>319</th>
      <td>Maryland</td>
      <td>2.194444e+05</td>
    </tr>
    <tr>
      <th>830</th>
      <td>Virginia</td>
      <td>1.908519e+05</td>
    </tr>
    <tr>
      <th>318</th>
      <td>Maine</td>
      <td>1.763704e+05</td>
    </tr>
    <tr>
      <th>808</th>
      <td>Kentucky</td>
      <td>1.240000e+05</td>
    </tr>
  </tbody>
</table>
</div>




```python
## create plot
from plotnine import ggplot, aes, geom_line

ggplot(honey) + aes(x="year",y='production',color = 'state') + geom_line()
```


    
![png](output_11_0.png)
    





    <ggplot: (8769669063605)>




```python
## because the above graph is hard to decipher, create a new dataset with the top six states
list_=['NorthDakota','California','SouthDakota','Florida','Montana','Minnesota']
top_six = honey.loc[honey['state'].isin(list_)]

#recreate plot
from plotnine import ggplot, aes, geom_line

ggplot(top_six) + aes(x="year",y='production',color = 'state') + geom_line()
```


    
![png](output_12_0.png)
    





    <ggplot: (8769687352564)>



##### Currently, the state with the highest production is south dakota. These six states have consistently had the highest production. 

### What is the distribution in the number of colonies at sights in the top 6 beekeeping states?


```python
## import geom_point()
from plotnine import ggplot, aes, geom_point
```


```python
## because the above graph is hard to decipher, create a new dataset with the top six states
list_=['NorthDakota','California','SouthDakota','Florida','Montana','Minnesota']
top_six = honey.loc[honey['state'].isin(list_)]

#recreate plot
from plotnine import ggplot, aes, geom_line

ggplot(top_six) + aes(x="state",y='colonies_number') + geom_point()
```


    
![png](output_16_0.png)
    





    <ggplot: (8782293936628)>



##### North Dakota has the greatest distribution in the number of colonies at various locations in the state. California also has a broader distribution in colony size. 

### How has the price of honey changed over time?


```python
## calculate the mean price by year
honey['mean.price'] = honey.groupby('year')['average_price'].transform('mean')
honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.production.state</th>
      <th>mean.average_price</th>
      <th>mean.price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>NorthDakota</td>
      <td>220000</td>
      <td>108</td>
      <td>23760000</td>
      <td>3802000</td>
      <td>63.00</td>
      <td>14969000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>1.902748e+07</td>
      <td>74.840909</td>
      <td>74.840909</td>
    </tr>
    <tr>
      <th>1100</th>
      <td>1100</td>
      <td>NorthDakota</td>
      <td>515000</td>
      <td>55</td>
      <td>2266000</td>
      <td>2266000</td>
      <td>2.19</td>
      <td>62032000</td>
      <td>2021</td>
      <td>46.700000</td>
      <td>1.902748e+07</td>
      <td>3.334250</td>
      <td>3.334250</td>
    </tr>
    <tr>
      <th>288</th>
      <td>288</td>
      <td>NorthDakota</td>
      <td>280000</td>
      <td>96</td>
      <td>26880000</td>
      <td>9408000</td>
      <td>65.00</td>
      <td>17472000</td>
      <td>2001</td>
      <td>65.209302</td>
      <td>1.902748e+07</td>
      <td>88.465116</td>
      <td>88.465116</td>
    </tr>
    <tr>
      <th>499</th>
      <td>499</td>
      <td>NorthDakota</td>
      <td>350000</td>
      <td>74</td>
      <td>25900000</td>
      <td>7770000</td>
      <td>90.00</td>
      <td>23310000</td>
      <td>2006</td>
      <td>61.853659</td>
      <td>1.902748e+07</td>
      <td>134.341463</td>
      <td>134.341463</td>
    </tr>
    <tr>
      <th>331</th>
      <td>331</td>
      <td>NorthDakota</td>
      <td>320000</td>
      <td>75</td>
      <td>24000000</td>
      <td>8160000</td>
      <td>142.00</td>
      <td>34080000</td>
      <td>2002</td>
      <td>67.272727</td>
      <td>1.902748e+07</td>
      <td>133.204545</td>
      <td>133.204545</td>
    </tr>
    <tr>
      <th>860</th>
      <td>860</td>
      <td>NorthDakota</td>
      <td>490000</td>
      <td>74</td>
      <td>9428000</td>
      <td>9428000</td>
      <td>180.00</td>
      <td>65268000</td>
      <td>2015</td>
      <td>55.325000</td>
      <td>1.902748e+07</td>
      <td>292.625000</td>
      <td>292.625000</td>
    </tr>
    <tr>
      <th>375</th>
      <td>375</td>
      <td>NorthDakota</td>
      <td>340000</td>
      <td>87</td>
      <td>29580000</td>
      <td>6803000</td>
      <td>136.00</td>
      <td>40229000</td>
      <td>2003</td>
      <td>62.522727</td>
      <td>1.902748e+07</td>
      <td>151.068182</td>
      <td>151.068182</td>
    </tr>
    <tr>
      <th>458</th>
      <td>458</td>
      <td>NorthDakota</td>
      <td>370000</td>
      <td>91</td>
      <td>33670000</td>
      <td>8418000</td>
      <td>81.00</td>
      <td>27273000</td>
      <td>2005</td>
      <td>64.268293</td>
      <td>1.902748e+07</td>
      <td>116.341463</td>
      <td>116.341463</td>
    </tr>
    <tr>
      <th>72</th>
      <td>72</td>
      <td>NorthDakota</td>
      <td>230000</td>
      <td>86</td>
      <td>19780000</td>
      <td>4945000</td>
      <td>90.00</td>
      <td>17802000</td>
      <td>1996</td>
      <td>70.068182</td>
      <td>1.902748e+07</td>
      <td>99.568182</td>
      <td>99.568182</td>
    </tr>
    <tr>
      <th>820</th>
      <td>820</td>
      <td>NorthDakota</td>
      <td>490000</td>
      <td>86</td>
      <td>9271000</td>
      <td>9271000</td>
      <td>199.00</td>
      <td>83859000</td>
      <td>2014</td>
      <td>57.350000</td>
      <td>1.902748e+07</td>
      <td>282.025000</td>
      <td>282.025000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# create plot
from plotnine import ggplot, aes, geom_line

ggplot(honey) + aes(x="year",y='mean.price') + geom_line()
```


    
![png](output_20_0.png)
    





    <ggplot: (8769696300698)>



##### The price of honey has (almost exponentially) increased throughout time. 

### How has the total production changed?


```python
honey['mean.production'] = honey.groupby('year')['production'].transform('mean')
honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.production.state</th>
      <th>mean.average_price</th>
      <th>mean.price</th>
      <th>mean.production</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>NorthDakota</td>
      <td>220000</td>
      <td>108</td>
      <td>23760000</td>
      <td>3802000</td>
      <td>63.00</td>
      <td>14969000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>1.902748e+07</td>
      <td>74.840909</td>
      <td>74.840909</td>
      <td>4.778909e+06</td>
    </tr>
    <tr>
      <th>1100</th>
      <td>1100</td>
      <td>NorthDakota</td>
      <td>515000</td>
      <td>55</td>
      <td>2266000</td>
      <td>2266000</td>
      <td>2.19</td>
      <td>62032000</td>
      <td>2021</td>
      <td>46.700000</td>
      <td>1.902748e+07</td>
      <td>3.334250</td>
      <td>3.334250</td>
      <td>5.796750e+05</td>
    </tr>
    <tr>
      <th>288</th>
      <td>288</td>
      <td>NorthDakota</td>
      <td>280000</td>
      <td>96</td>
      <td>26880000</td>
      <td>9408000</td>
      <td>65.00</td>
      <td>17472000</td>
      <td>2001</td>
      <td>65.209302</td>
      <td>1.902748e+07</td>
      <td>88.465116</td>
      <td>88.465116</td>
      <td>4.311698e+06</td>
    </tr>
    <tr>
      <th>499</th>
      <td>499</td>
      <td>NorthDakota</td>
      <td>350000</td>
      <td>74</td>
      <td>25900000</td>
      <td>7770000</td>
      <td>90.00</td>
      <td>23310000</td>
      <td>2006</td>
      <td>61.853659</td>
      <td>1.902748e+07</td>
      <td>134.341463</td>
      <td>134.341463</td>
      <td>3.759024e+06</td>
    </tr>
    <tr>
      <th>331</th>
      <td>331</td>
      <td>NorthDakota</td>
      <td>320000</td>
      <td>75</td>
      <td>24000000</td>
      <td>8160000</td>
      <td>142.00</td>
      <td>34080000</td>
      <td>2002</td>
      <td>67.272727</td>
      <td>1.902748e+07</td>
      <td>133.204545</td>
      <td>133.204545</td>
      <td>3.880273e+06</td>
    </tr>
    <tr>
      <th>860</th>
      <td>860</td>
      <td>NorthDakota</td>
      <td>490000</td>
      <td>74</td>
      <td>9428000</td>
      <td>9428000</td>
      <td>180.00</td>
      <td>65268000</td>
      <td>2015</td>
      <td>55.325000</td>
      <td>1.902748e+07</td>
      <td>292.625000</td>
      <td>292.625000</td>
      <td>1.045800e+06</td>
    </tr>
    <tr>
      <th>375</th>
      <td>375</td>
      <td>NorthDakota</td>
      <td>340000</td>
      <td>87</td>
      <td>29580000</td>
      <td>6803000</td>
      <td>136.00</td>
      <td>40229000</td>
      <td>2003</td>
      <td>62.522727</td>
      <td>1.902748e+07</td>
      <td>151.068182</td>
      <td>151.068182</td>
      <td>4.107750e+06</td>
    </tr>
    <tr>
      <th>458</th>
      <td>458</td>
      <td>NorthDakota</td>
      <td>370000</td>
      <td>91</td>
      <td>33670000</td>
      <td>8418000</td>
      <td>81.00</td>
      <td>27273000</td>
      <td>2005</td>
      <td>64.268293</td>
      <td>1.902748e+07</td>
      <td>116.341463</td>
      <td>116.341463</td>
      <td>4.240415e+06</td>
    </tr>
    <tr>
      <th>72</th>
      <td>72</td>
      <td>NorthDakota</td>
      <td>230000</td>
      <td>86</td>
      <td>19780000</td>
      <td>4945000</td>
      <td>90.00</td>
      <td>17802000</td>
      <td>1996</td>
      <td>70.068182</td>
      <td>1.902748e+07</td>
      <td>99.568182</td>
      <td>99.568182</td>
      <td>4.499886e+06</td>
    </tr>
    <tr>
      <th>820</th>
      <td>820</td>
      <td>NorthDakota</td>
      <td>490000</td>
      <td>86</td>
      <td>9271000</td>
      <td>9271000</td>
      <td>199.00</td>
      <td>83859000</td>
      <td>2014</td>
      <td>57.350000</td>
      <td>1.902748e+07</td>
      <td>282.025000</td>
      <td>282.025000</td>
      <td>1.024750e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
from plotnine import ggplot, aes, geom_line

ggplot(honey) + aes(x="year",y='mean.production') + geom_line()
```


    
![png](output_24_0.png)
    





    <ggplot: (8769709020868)>



##### In 2006, the production dropped drastically. Since then, production has stayed the same but stayed much lower than previously. This data is consistent with the phenomonen known as the colony collapse disorder, which happened in 2006, where there was a drastic decrease in the health and number of bees. 

### How many colonies are there now?


```python
honey['mean.numbercolonies'] = honey.groupby('year')['colonies_number'].transform('mean')
honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.production.state</th>
      <th>mean.average_price</th>
      <th>mean.price</th>
      <th>mean.production</th>
      <th>mean.numbercolonies</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>NorthDakota</td>
      <td>220000</td>
      <td>108</td>
      <td>23760000</td>
      <td>3802000</td>
      <td>63.00</td>
      <td>14969000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>1.902748e+07</td>
      <td>74.840909</td>
      <td>74.840909</td>
      <td>4.778909e+06</td>
      <td>59977.272727</td>
    </tr>
    <tr>
      <th>1100</th>
      <td>1100</td>
      <td>NorthDakota</td>
      <td>515000</td>
      <td>55</td>
      <td>2266000</td>
      <td>2266000</td>
      <td>2.19</td>
      <td>62032000</td>
      <td>2021</td>
      <td>46.700000</td>
      <td>1.902748e+07</td>
      <td>3.334250</td>
      <td>3.334250</td>
      <td>5.796750e+05</td>
      <td>66700.000000</td>
    </tr>
    <tr>
      <th>288</th>
      <td>288</td>
      <td>NorthDakota</td>
      <td>280000</td>
      <td>96</td>
      <td>26880000</td>
      <td>9408000</td>
      <td>65.00</td>
      <td>17472000</td>
      <td>2001</td>
      <td>65.209302</td>
      <td>1.902748e+07</td>
      <td>88.465116</td>
      <td>88.465116</td>
      <td>4.311698e+06</td>
      <td>58139.534884</td>
    </tr>
    <tr>
      <th>499</th>
      <td>499</td>
      <td>NorthDakota</td>
      <td>350000</td>
      <td>74</td>
      <td>25900000</td>
      <td>7770000</td>
      <td>90.00</td>
      <td>23310000</td>
      <td>2006</td>
      <td>61.853659</td>
      <td>1.902748e+07</td>
      <td>134.341463</td>
      <td>134.341463</td>
      <td>3.759024e+06</td>
      <td>57926.829268</td>
    </tr>
    <tr>
      <th>331</th>
      <td>331</td>
      <td>NorthDakota</td>
      <td>320000</td>
      <td>75</td>
      <td>24000000</td>
      <td>8160000</td>
      <td>142.00</td>
      <td>34080000</td>
      <td>2002</td>
      <td>67.272727</td>
      <td>1.902748e+07</td>
      <td>133.204545</td>
      <td>133.204545</td>
      <td>3.880273e+06</td>
      <td>57181.818182</td>
    </tr>
    <tr>
      <th>860</th>
      <td>860</td>
      <td>NorthDakota</td>
      <td>490000</td>
      <td>74</td>
      <td>9428000</td>
      <td>9428000</td>
      <td>180.00</td>
      <td>65268000</td>
      <td>2015</td>
      <td>55.325000</td>
      <td>1.902748e+07</td>
      <td>292.625000</td>
      <td>292.625000</td>
      <td>1.045800e+06</td>
      <td>65750.000000</td>
    </tr>
    <tr>
      <th>375</th>
      <td>375</td>
      <td>NorthDakota</td>
      <td>340000</td>
      <td>87</td>
      <td>29580000</td>
      <td>6803000</td>
      <td>136.00</td>
      <td>40229000</td>
      <td>2003</td>
      <td>62.522727</td>
      <td>1.902748e+07</td>
      <td>151.068182</td>
      <td>151.068182</td>
      <td>4.107750e+06</td>
      <td>58681.818182</td>
    </tr>
    <tr>
      <th>458</th>
      <td>458</td>
      <td>NorthDakota</td>
      <td>370000</td>
      <td>91</td>
      <td>33670000</td>
      <td>8418000</td>
      <td>81.00</td>
      <td>27273000</td>
      <td>2005</td>
      <td>64.268293</td>
      <td>1.902748e+07</td>
      <td>116.341463</td>
      <td>116.341463</td>
      <td>4.240415e+06</td>
      <td>58341.463415</td>
    </tr>
    <tr>
      <th>72</th>
      <td>72</td>
      <td>NorthDakota</td>
      <td>230000</td>
      <td>86</td>
      <td>19780000</td>
      <td>4945000</td>
      <td>90.00</td>
      <td>17802000</td>
      <td>1996</td>
      <td>70.068182</td>
      <td>1.902748e+07</td>
      <td>99.568182</td>
      <td>99.568182</td>
      <td>4.499886e+06</td>
      <td>58181.818182</td>
    </tr>
    <tr>
      <th>820</th>
      <td>820</td>
      <td>NorthDakota</td>
      <td>490000</td>
      <td>86</td>
      <td>9271000</td>
      <td>9271000</td>
      <td>199.00</td>
      <td>83859000</td>
      <td>2014</td>
      <td>57.350000</td>
      <td>1.902748e+07</td>
      <td>282.025000</td>
      <td>282.025000</td>
      <td>1.024750e+06</td>
      <td>67725.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
from plotnine import ggplot, aes, geom_line

ggplot(honey) + aes(x="year",y='mean.numbercolonies') + geom_line()
```


    
![png](output_28_0.png)
    





    <ggplot: (8769709363993)>



##### the number of colonies is steadily rising, even as population numbers decrease. This is likely because more colonies are needed to keep up with demand. 

### How has the value of production changed over time?


```python
## calculate the mean value of production per year
honey['mean.value_of_production'] = honey.groupby('year')['value_of_production'].transform('mean')
honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.yield</th>
      <th>mean.value_of_production</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Alabama</td>
      <td>16000</td>
      <td>58</td>
      <td>928000</td>
      <td>28000</td>
      <td>62.0</td>
      <td>575000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Arizona</td>
      <td>52000</td>
      <td>79</td>
      <td>4108000</td>
      <td>986000</td>
      <td>68.0</td>
      <td>2793000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Arkansas</td>
      <td>50000</td>
      <td>60</td>
      <td>3000000</td>
      <td>900000</td>
      <td>64.0</td>
      <td>1920000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>California</td>
      <td>420000</td>
      <td>93</td>
      <td>39060000</td>
      <td>4687000</td>
      <td>60.0</td>
      <td>23436000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Colorado</td>
      <td>45000</td>
      <td>60</td>
      <td>2700000</td>
      <td>1404000</td>
      <td>68.0</td>
      <td>1836000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Florida</td>
      <td>230000</td>
      <td>86</td>
      <td>19780000</td>
      <td>1780000</td>
      <td>63.0</td>
      <td>12461000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Georgia</td>
      <td>70000</td>
      <td>62</td>
      <td>4340000</td>
      <td>260000</td>
      <td>69.0</td>
      <td>2995000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Hawaii</td>
      <td>8000</td>
      <td>129</td>
      <td>1032000</td>
      <td>103000</td>
      <td>55.0</td>
      <td>568000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Idaho</td>
      <td>125000</td>
      <td>48</td>
      <td>6000000</td>
      <td>1020000</td>
      <td>65.0</td>
      <td>3900000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Illinois</td>
      <td>11000</td>
      <td>74</td>
      <td>814000</td>
      <td>212000</td>
      <td>102.0</td>
      <td>830000</td>
      <td>1995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
from plotnine import ggplot, aes, geom_line

ggplot(honey) + aes(x="year",y='mean.value_of_production') + geom_line()
```


    
![png](output_32_0.png)
    





    <ggplot: (8782312270126)>



##### the value of production has gone up until around 2013, but has seemed to decrease since then. 

### In which states, is production increasing since the crisis in 2006?


```python
# convert the 'Date' column to datetime format
##honey['year'] = pd.to_datetime(honey['year'], format='%Y')
honey.info()
honey.head(10)
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1115 entries, 0 to 1114
    Data columns (total 12 columns):
     #   Column                    Non-Null Count  Dtype         
    ---  ------                    --------------  -----         
     0   Unnamed: 0                1115 non-null   int64         
     1   state                     1115 non-null   object        
     2   colonies_number           1115 non-null   int64         
     3   yield_per_colony          1115 non-null   int64         
     4   production                1115 non-null   int64         
     5   stocks                    1115 non-null   int64         
     6   average_price             1115 non-null   float64       
     7   value_of_production       1115 non-null   int64         
     8   year                      1115 non-null   datetime64[ns]
     9   mean.year                 1115 non-null   float64       
     10  mean.yield                1115 non-null   float64       
     11  mean.value_of_production  1115 non-null   float64       
    dtypes: datetime64[ns](1), float64(4), int64(6), object(1)
    memory usage: 104.7+ KB





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.yield</th>
      <th>mean.value_of_production</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Alabama</td>
      <td>16000</td>
      <td>58</td>
      <td>928000</td>
      <td>28000</td>
      <td>62.0</td>
      <td>575000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Arizona</td>
      <td>52000</td>
      <td>79</td>
      <td>4108000</td>
      <td>986000</td>
      <td>68.0</td>
      <td>2793000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Arkansas</td>
      <td>50000</td>
      <td>60</td>
      <td>3000000</td>
      <td>900000</td>
      <td>64.0</td>
      <td>1920000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>California</td>
      <td>420000</td>
      <td>93</td>
      <td>39060000</td>
      <td>4687000</td>
      <td>60.0</td>
      <td>23436000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Colorado</td>
      <td>45000</td>
      <td>60</td>
      <td>2700000</td>
      <td>1404000</td>
      <td>68.0</td>
      <td>1836000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Florida</td>
      <td>230000</td>
      <td>86</td>
      <td>19780000</td>
      <td>1780000</td>
      <td>63.0</td>
      <td>12461000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Georgia</td>
      <td>70000</td>
      <td>62</td>
      <td>4340000</td>
      <td>260000</td>
      <td>69.0</td>
      <td>2995000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Hawaii</td>
      <td>8000</td>
      <td>129</td>
      <td>1032000</td>
      <td>103000</td>
      <td>55.0</td>
      <td>568000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Idaho</td>
      <td>125000</td>
      <td>48</td>
      <td>6000000</td>
      <td>1020000</td>
      <td>65.0</td>
      <td>3900000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Illinois</td>
      <td>11000</td>
      <td>74</td>
      <td>814000</td>
      <td>212000</td>
      <td>102.0</td>
      <td>830000</td>
      <td>1970-01-01 00:00:00.000001995</td>
      <td>66.909091</td>
      <td>66.909091</td>
      <td>3121000.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
filtered_honey = honey.loc[(honey['year'] >= '2006-01-01')]
filtered_honey.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>state</th>
      <th>colonies_number</th>
      <th>yield_per_colony</th>
      <th>production</th>
      <th>stocks</th>
      <th>average_price</th>
      <th>value_of_production</th>
      <th>year</th>
      <th>mean.year</th>
      <th>mean.yield</th>
      <th>mean.value_of_production</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
## create plot
from plotnine import ggplot, aes, geom_line

ggplot(filtered_honey) + aes(x="year",y='production',color = 'state') + geom_line()
```


    
![png](output_37_0.png)
    





    <ggplot: (8782243747094)>




```python

```
