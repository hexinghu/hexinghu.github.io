---
title: pandas学习教程
date: 2019-09-02 17:17:03
categories:
    -python
tags:
    - python
    - pandas
    - 数据分析
    - 机器学习
---

# 1. Series

seriers 类似于具名一维数组
<!--more-->

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.font_manager import FontManager
```


```python
a = np.linspace(0,100,1000,dtype=np.int16)
s = pd.Series(a,index=[i for i in range(len(a))])
```


```python
s
```




    0        0
    1        0
    2        0
    3        0
    4        0
    5        0
    6        0
    7        0
    8        0
    9        0
    10       1
    11       1
    12       1
    13       1
    14       1
    15       1
    16       1
    17       1
    18       1
    19       1
    20       2
    21       2
    22       2
    23       2
    24       2
    25       2
    26       2
    27       2
    28       2
    29       2
          ... 
    970     97
    971     97
    972     97
    973     97
    974     97
    975     97
    976     97
    977     97
    978     97
    979     97
    980     98
    981     98
    982     98
    983     98
    984     98
    985     98
    986     98
    987     98
    988     98
    989     98
    990     99
    991     99
    992     99
    993     99
    994     99
    995     99
    996     99
    997     99
    998     99
    999    100
    Length: 1000, dtype: int16




```python
%matplotlib inline
s.plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210d8895be0>




![png](http://px6vw3ifw.bkt.clouddn.com/output_5_1.png)



```python
s2 = pd.Series({"小明":20,"小华":30,"张磊":40},name="s2")
```


```python
s2
```




    小明    20
    小华    30
    张磊    40
    Name: s2, dtype: int64




```python
s2.plot(kind="pie")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210da794390>




![png](http://px6vw3ifw.bkt.clouddn.com/output_8_1.png)



```python
s2.__dict__
```




    {'_is_copy': None, '_data': SingleBlockManager
     Items: Index(['小明', '小华', '张磊'], dtype='object')
     IntBlock: 3 dtype: int64, '_item_cache': {}, '_name': 's2', '_subtyp': 'series', '_index': Index(['小明', '小华', '张磊'], dtype='object'), 'plot': <pandas.plotting._core.SeriesPlotMethods object at 0x00000210DA6DA860>}




```python
a = pd.read_csv("heart.csv")
```


```python
a.head(10)
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
      <th>age</th>
      <th>sex</th>
      <th>cp</th>
      <th>trestbps</th>
      <th>chol</th>
      <th>fbs</th>
      <th>restecg</th>
      <th>thalach</th>
      <th>exang</th>
      <th>oldpeak</th>
      <th>slope</th>
      <th>ca</th>
      <th>thal</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>63</td>
      <td>1</td>
      <td>3</td>
      <td>145</td>
      <td>233</td>
      <td>1</td>
      <td>0</td>
      <td>150</td>
      <td>0</td>
      <td>2.3</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>37</td>
      <td>1</td>
      <td>2</td>
      <td>130</td>
      <td>250</td>
      <td>0</td>
      <td>1</td>
      <td>187</td>
      <td>0</td>
      <td>3.5</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41</td>
      <td>0</td>
      <td>1</td>
      <td>130</td>
      <td>204</td>
      <td>0</td>
      <td>0</td>
      <td>172</td>
      <td>0</td>
      <td>1.4</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>56</td>
      <td>1</td>
      <td>1</td>
      <td>120</td>
      <td>236</td>
      <td>0</td>
      <td>1</td>
      <td>178</td>
      <td>0</td>
      <td>0.8</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>57</td>
      <td>0</td>
      <td>0</td>
      <td>120</td>
      <td>354</td>
      <td>0</td>
      <td>1</td>
      <td>163</td>
      <td>1</td>
      <td>0.6</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>57</td>
      <td>1</td>
      <td>0</td>
      <td>140</td>
      <td>192</td>
      <td>0</td>
      <td>1</td>
      <td>148</td>
      <td>0</td>
      <td>0.4</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>56</td>
      <td>0</td>
      <td>1</td>
      <td>140</td>
      <td>294</td>
      <td>0</td>
      <td>0</td>
      <td>153</td>
      <td>0</td>
      <td>1.3</td>
      <td>1</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>7</th>
      <td>44</td>
      <td>1</td>
      <td>1</td>
      <td>120</td>
      <td>263</td>
      <td>0</td>
      <td>1</td>
      <td>173</td>
      <td>0</td>
      <td>0.0</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
      <td>1</td>
    </tr>
    <tr>
      <th>8</th>
      <td>52</td>
      <td>1</td>
      <td>2</td>
      <td>172</td>
      <td>199</td>
      <td>1</td>
      <td>1</td>
      <td>162</td>
      <td>0</td>
      <td>0.5</td>
      <td>2</td>
      <td>0</td>
      <td>3</td>
      <td>1</td>
    </tr>
    <tr>
      <th>9</th>
      <td>57</td>
      <td>1</td>
      <td>2</td>
      <td>150</td>
      <td>168</td>
      <td>0</td>
      <td>1</td>
      <td>174</td>
      <td>0</td>
      <td>1.6</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
a[["age","cp","chol"]].plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210dbd67278>




![png](http://px6vw3ifw.bkt.clouddn.com/output_12_1.png)



```python
a[["sex","cp","ca"]].plot.box()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210dbf599b0>




![png](http://px6vw3ifw.bkt.clouddn.com/output_13_1.png)



```python
a[["sex","cp","ca"]].plot.bar()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210dc0bab38>




![png](http://px6vw3ifw.bkt.clouddn.com/output_14_1.png)



```python
a.count()
```




    age         303
    sex         303
    cp          303
    trestbps    303
    chol        303
    fbs         303
    restecg     303
    thalach     303
    exang       303
    oldpeak     303
    slope       303
    ca          303
    thal        303
    target      303
    dtype: int64




```python
a.sum(axis=0)
```




    age         16473.0
    sex           207.0
    cp            293.0
    trestbps    39882.0
    chol        74618.0
    fbs            45.0
    restecg       160.0
    thalach     45343.0
    exang          99.0
    oldpeak       315.0
    slope         424.0
    ca            221.0
    thal          701.0
    target        165.0
    dtype: float64




```python
type(a)
```




    pandas.core.frame.DataFrame



# 2. DataFrame

DataFrame类似于一张Excel表格


```python
data = pd.DataFrame(np.random.randint(0,50,(10,5)),columns=list("ABCDE"))
```


```python
data
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>24</td>
      <td>12</td>
      <td>3</td>
      <td>45</td>
      <td>14</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13</td>
      <td>31</td>
      <td>36</td>
      <td>26</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>48</td>
      <td>17</td>
      <td>3</td>
      <td>6</td>
      <td>43</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>6</td>
      <td>9</td>
      <td>23</td>
      <td>6</td>
    </tr>
    <tr>
      <th>4</th>
      <td>13</td>
      <td>26</td>
      <td>21</td>
      <td>5</td>
      <td>13</td>
    </tr>
    <tr>
      <th>5</th>
      <td>30</td>
      <td>44</td>
      <td>24</td>
      <td>8</td>
      <td>29</td>
    </tr>
    <tr>
      <th>6</th>
      <td>19</td>
      <td>18</td>
      <td>45</td>
      <td>48</td>
      <td>28</td>
    </tr>
    <tr>
      <th>7</th>
      <td>32</td>
      <td>5</td>
      <td>39</td>
      <td>0</td>
      <td>13</td>
    </tr>
    <tr>
      <th>8</th>
      <td>45</td>
      <td>32</td>
      <td>25</td>
      <td>26</td>
      <td>41</td>
    </tr>
    <tr>
      <th>9</th>
      <td>12</td>
      <td>23</td>
      <td>39</td>
      <td>12</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.cumsum().plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210e14ffcf8>




![png](http://px6vw3ifw.bkt.clouddn.com/output_22_1.png)



```python
data2 = pd.DataFrame(np.random.randn(50,10),columns=list("ABCKEKFGHI"))
```


```python
data2.head(5).cumsum().plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210e2ca60b8>




![png](http://px6vw3ifw.bkt.clouddn.com/output_24_1.png)



```python
data2.head(5).plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x210e1c4f6a0>




![png](http://px6vw3ifw.bkt.clouddn.com/output_25_1.png)



```python
data2.iloc[::2,:].head(5)
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>K</th>
      <th>E</th>
      <th>K</th>
      <th>F</th>
      <th>G</th>
      <th>H</th>
      <th>I</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.393696</td>
      <td>-0.662632</td>
      <td>0.185510</td>
      <td>0.705006</td>
      <td>0.826794</td>
      <td>1.676754</td>
      <td>-0.430697</td>
      <td>-0.191531</td>
      <td>-0.843572</td>
      <td>1.097599</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.135932</td>
      <td>0.030360</td>
      <td>0.632720</td>
      <td>-1.005872</td>
      <td>0.073344</td>
      <td>1.091800</td>
      <td>-0.551436</td>
      <td>1.112981</td>
      <td>0.902193</td>
      <td>-0.315091</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-1.529747</td>
      <td>-0.010646</td>
      <td>0.876781</td>
      <td>-0.326180</td>
      <td>-1.279786</td>
      <td>-1.586761</td>
      <td>3.437710</td>
      <td>0.023980</td>
      <td>0.867506</td>
      <td>0.180815</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.982361</td>
      <td>-0.366534</td>
      <td>0.273448</td>
      <td>0.249000</td>
      <td>-0.626764</td>
      <td>-1.191071</td>
      <td>-0.919671</td>
      <td>-0.251107</td>
      <td>-0.213945</td>
      <td>1.700244</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-1.911405</td>
      <td>-0.211032</td>
      <td>0.042495</td>
      <td>1.049690</td>
      <td>1.303780</td>
      <td>-0.916393</td>
      <td>0.796054</td>
      <td>1.375747</td>
      <td>-1.242015</td>
      <td>1.675148</td>
    </tr>
  </tbody>
</table>
</div>




```python
data2.iloc[::2,::2].head(5)
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
      <th>A</th>
      <th>C</th>
      <th>E</th>
      <th>F</th>
      <th>H</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.393696</td>
      <td>0.185510</td>
      <td>0.826794</td>
      <td>-0.430697</td>
      <td>-0.843572</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.135932</td>
      <td>0.632720</td>
      <td>0.073344</td>
      <td>-0.551436</td>
      <td>0.902193</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-1.529747</td>
      <td>0.876781</td>
      <td>-1.279786</td>
      <td>3.437710</td>
      <td>0.867506</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.982361</td>
      <td>0.273448</td>
      <td>-0.626764</td>
      <td>-0.919671</td>
      <td>-0.213945</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-1.911405</td>
      <td>0.042495</td>
      <td>1.303780</td>
      <td>0.796054</td>
      <td>-1.242015</td>
    </tr>
  </tbody>
</table>
</div>




```python
data2.mean()
```




    A    0.215457
    B   -0.413272
    C    0.167236
    K    0.027997
    E   -0.163819
    K   -0.116619
    F    0.111577
    G    0.046912
    H   -0.049657
    I    0.042516
    dtype: float64




```python
data2.max()
```




    A    2.887807
    B    3.246349
    C    1.824274
    K    2.198626
    E    1.885702
    K    1.853781
    F    3.437710
    G    1.475031
    H    2.516398
    I    2.417594
    dtype: float64

    

```python
data = pd.read_csv("heart.csv")
```


```python
data.head()
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
      <th>age</th>
      <th>sex</th>
      <th>cp</th>
      <th>trestbps</th>
      <th>chol</th>
      <th>fbs</th>
      <th>restecg</th>
      <th>thalach</th>
      <th>exang</th>
      <th>oldpeak</th>
      <th>slope</th>
      <th>ca</th>
      <th>thal</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>63</td>
      <td>1</td>
      <td>3</td>
      <td>145</td>
      <td>233</td>
      <td>1</td>
      <td>0</td>
      <td>150</td>
      <td>0</td>
      <td>2.3</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>37</td>
      <td>1</td>
      <td>2</td>
      <td>130</td>
      <td>250</td>
      <td>0</td>
      <td>1</td>
      <td>187</td>
      <td>0</td>
      <td>3.5</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41</td>
      <td>0</td>
      <td>1</td>
      <td>130</td>
      <td>204</td>
      <td>0</td>
      <td>0</td>
      <td>172</td>
      <td>0</td>
      <td>1.4</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>56</td>
      <td>1</td>
      <td>1</td>
      <td>120</td>
      <td>236</td>
      <td>0</td>
      <td>1</td>
      <td>178</td>
      <td>0</td>
      <td>0.8</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>57</td>
      <td>0</td>
      <td>0</td>
      <td>120</td>
      <td>354</td>
      <td>0</td>
      <td>1</td>
      <td>163</td>
      <td>1</td>
      <td>0.6</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.tail()
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
      <th>age</th>
      <th>sex</th>
      <th>cp</th>
      <th>trestbps</th>
      <th>chol</th>
      <th>fbs</th>
      <th>restecg</th>
      <th>thalach</th>
      <th>exang</th>
      <th>oldpeak</th>
      <th>slope</th>
      <th>ca</th>
      <th>thal</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>298</th>
      <td>57</td>
      <td>0</td>
      <td>0</td>
      <td>140</td>
      <td>241</td>
      <td>0</td>
      <td>1</td>
      <td>123</td>
      <td>1</td>
      <td>0.2</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>299</th>
      <td>45</td>
      <td>1</td>
      <td>3</td>
      <td>110</td>
      <td>264</td>
      <td>0</td>
      <td>1</td>
      <td>132</td>
      <td>0</td>
      <td>1.2</td>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>300</th>
      <td>68</td>
      <td>1</td>
      <td>0</td>
      <td>144</td>
      <td>193</td>
      <td>1</td>
      <td>1</td>
      <td>141</td>
      <td>0</td>
      <td>3.4</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>301</th>
      <td>57</td>
      <td>1</td>
      <td>0</td>
      <td>130</td>
      <td>131</td>
      <td>0</td>
      <td>1</td>
      <td>115</td>
      <td>1</td>
      <td>1.2</td>
      <td>1</td>
      <td>1</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>302</th>
      <td>57</td>
      <td>0</td>
      <td>1</td>
      <td>130</td>
      <td>236</td>
      <td>0</td>
      <td>0</td>
      <td>174</td>
      <td>0</td>
      <td>0.0</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data['age'].head()
```




    0    63
    1    37
    2    41
    3    56
    4    57
    Name: age, dtype: int64




```python
data[['age','sex']].tail()
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
      <th>age</th>
      <th>sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>298</th>
      <td>57</td>
      <td>0</td>
    </tr>
    <tr>
      <th>299</th>
      <td>45</td>
      <td>1</td>
    </tr>
    <tr>
      <th>300</th>
      <td>68</td>
      <td>1</td>
    </tr>
    <tr>
      <th>301</th>
      <td>57</td>
      <td>1</td>
    </tr>
    <tr>
      <th>302</th>
      <td>57</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
def fun(arg):
    return arg*8
```


```python
data.apply(fun)
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
      <th>age</th>
      <th>sex</th>
      <th>cp</th>
      <th>trestbps</th>
      <th>chol</th>
      <th>fbs</th>
      <th>restecg</th>
      <th>thalach</th>
      <th>exang</th>
      <th>oldpeak</th>
      <th>slope</th>
      <th>ca</th>
      <th>thal</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>504</td>
      <td>8</td>
      <td>24</td>
      <td>1160</td>
      <td>1864</td>
      <td>8</td>
      <td>0</td>
      <td>1200</td>
      <td>0</td>
      <td>18.4</td>
      <td>0</td>
      <td>0</td>
      <td>8</td>
      <td>8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>296</td>
      <td>8</td>
      <td>16</td>
      <td>1040</td>
      <td>2000</td>
      <td>0</td>
      <td>8</td>
      <td>1496</td>
      <td>0</td>
      <td>28.0</td>
      <td>0</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>328</td>
      <td>0</td>
      <td>8</td>
      <td>1040</td>
      <td>1632</td>
      <td>0</td>
      <td>0</td>
      <td>1376</td>
      <td>0</td>
      <td>11.2</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>448</td>
      <td>8</td>
      <td>8</td>
      <td>960</td>
      <td>1888</td>
      <td>0</td>
      <td>8</td>
      <td>1424</td>
      <td>0</td>
      <td>6.4</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>456</td>
      <td>0</td>
      <td>0</td>
      <td>960</td>
      <td>2832</td>
      <td>0</td>
      <td>8</td>
      <td>1304</td>
      <td>8</td>
      <td>4.8</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>5</th>
      <td>456</td>
      <td>8</td>
      <td>0</td>
      <td>1120</td>
      <td>1536</td>
      <td>0</td>
      <td>8</td>
      <td>1184</td>
      <td>0</td>
      <td>3.2</td>
      <td>8</td>
      <td>0</td>
      <td>8</td>
      <td>8</td>
    </tr>
    <tr>
      <th>6</th>
      <td>448</td>
      <td>0</td>
      <td>8</td>
      <td>1120</td>
      <td>2352</td>
      <td>0</td>
      <td>0</td>
      <td>1224</td>
      <td>0</td>
      <td>10.4</td>
      <td>8</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>7</th>
      <td>352</td>
      <td>8</td>
      <td>8</td>
      <td>960</td>
      <td>2104</td>
      <td>0</td>
      <td>8</td>
      <td>1384</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>0</td>
      <td>24</td>
      <td>8</td>
    </tr>
    <tr>
      <th>8</th>
      <td>416</td>
      <td>8</td>
      <td>16</td>
      <td>1376</td>
      <td>1592</td>
      <td>8</td>
      <td>8</td>
      <td>1296</td>
      <td>0</td>
      <td>4.0</td>
      <td>16</td>
      <td>0</td>
      <td>24</td>
      <td>8</td>
    </tr>
    <tr>
      <th>9</th>
      <td>456</td>
      <td>8</td>
      <td>16</td>
      <td>1200</td>
      <td>1344</td>
      <td>0</td>
      <td>8</td>
      <td>1392</td>
      <td>0</td>
      <td>12.8</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>10</th>
      <td>432</td>
      <td>8</td>
      <td>0</td>
      <td>1120</td>
      <td>1912</td>
      <td>0</td>
      <td>8</td>
      <td>1280</td>
      <td>0</td>
      <td>9.6</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>11</th>
      <td>384</td>
      <td>0</td>
      <td>16</td>
      <td>1040</td>
      <td>2200</td>
      <td>0</td>
      <td>8</td>
      <td>1112</td>
      <td>0</td>
      <td>1.6</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>12</th>
      <td>392</td>
      <td>8</td>
      <td>8</td>
      <td>1040</td>
      <td>2128</td>
      <td>0</td>
      <td>8</td>
      <td>1368</td>
      <td>0</td>
      <td>4.8</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>13</th>
      <td>512</td>
      <td>8</td>
      <td>24</td>
      <td>880</td>
      <td>1688</td>
      <td>0</td>
      <td>0</td>
      <td>1152</td>
      <td>8</td>
      <td>14.4</td>
      <td>8</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>14</th>
      <td>464</td>
      <td>0</td>
      <td>24</td>
      <td>1200</td>
      <td>2264</td>
      <td>8</td>
      <td>0</td>
      <td>1296</td>
      <td>0</td>
      <td>8.0</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>15</th>
      <td>400</td>
      <td>0</td>
      <td>16</td>
      <td>960</td>
      <td>1752</td>
      <td>0</td>
      <td>8</td>
      <td>1264</td>
      <td>0</td>
      <td>12.8</td>
      <td>8</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>16</th>
      <td>464</td>
      <td>0</td>
      <td>16</td>
      <td>960</td>
      <td>2720</td>
      <td>0</td>
      <td>8</td>
      <td>1376</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>17</th>
      <td>528</td>
      <td>0</td>
      <td>24</td>
      <td>1200</td>
      <td>1808</td>
      <td>0</td>
      <td>8</td>
      <td>912</td>
      <td>0</td>
      <td>20.8</td>
      <td>0</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>18</th>
      <td>344</td>
      <td>8</td>
      <td>0</td>
      <td>1200</td>
      <td>1976</td>
      <td>0</td>
      <td>8</td>
      <td>1368</td>
      <td>0</td>
      <td>12.0</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>19</th>
      <td>552</td>
      <td>0</td>
      <td>24</td>
      <td>1120</td>
      <td>1912</td>
      <td>0</td>
      <td>8</td>
      <td>1208</td>
      <td>0</td>
      <td>14.4</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>20</th>
      <td>472</td>
      <td>8</td>
      <td>0</td>
      <td>1080</td>
      <td>1872</td>
      <td>0</td>
      <td>8</td>
      <td>1288</td>
      <td>0</td>
      <td>4.0</td>
      <td>8</td>
      <td>0</td>
      <td>24</td>
      <td>8</td>
    </tr>
    <tr>
      <th>21</th>
      <td>352</td>
      <td>8</td>
      <td>16</td>
      <td>1040</td>
      <td>1864</td>
      <td>0</td>
      <td>8</td>
      <td>1432</td>
      <td>8</td>
      <td>3.2</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>22</th>
      <td>336</td>
      <td>8</td>
      <td>0</td>
      <td>1120</td>
      <td>1808</td>
      <td>0</td>
      <td>8</td>
      <td>1424</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>23</th>
      <td>488</td>
      <td>8</td>
      <td>16</td>
      <td>1200</td>
      <td>1944</td>
      <td>8</td>
      <td>8</td>
      <td>1096</td>
      <td>8</td>
      <td>8.0</td>
      <td>8</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>24</th>
      <td>320</td>
      <td>8</td>
      <td>24</td>
      <td>1120</td>
      <td>1592</td>
      <td>0</td>
      <td>8</td>
      <td>1424</td>
      <td>8</td>
      <td>11.2</td>
      <td>16</td>
      <td>0</td>
      <td>24</td>
      <td>8</td>
    </tr>
    <tr>
      <th>25</th>
      <td>568</td>
      <td>0</td>
      <td>8</td>
      <td>1280</td>
      <td>2416</td>
      <td>0</td>
      <td>8</td>
      <td>1296</td>
      <td>0</td>
      <td>3.2</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>26</th>
      <td>472</td>
      <td>8</td>
      <td>16</td>
      <td>1200</td>
      <td>1696</td>
      <td>8</td>
      <td>8</td>
      <td>1256</td>
      <td>0</td>
      <td>12.8</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>27</th>
      <td>408</td>
      <td>8</td>
      <td>16</td>
      <td>880</td>
      <td>1400</td>
      <td>0</td>
      <td>8</td>
      <td>984</td>
      <td>0</td>
      <td>4.8</td>
      <td>16</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>28</th>
      <td>520</td>
      <td>0</td>
      <td>16</td>
      <td>1120</td>
      <td>3336</td>
      <td>8</td>
      <td>0</td>
      <td>1256</td>
      <td>0</td>
      <td>6.4</td>
      <td>16</td>
      <td>8</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>29</th>
      <td>424</td>
      <td>8</td>
      <td>16</td>
      <td>1040</td>
      <td>1576</td>
      <td>8</td>
      <td>0</td>
      <td>1216</td>
      <td>0</td>
      <td>9.6</td>
      <td>0</td>
      <td>0</td>
      <td>16</td>
      <td>8</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>273</th>
      <td>464</td>
      <td>8</td>
      <td>0</td>
      <td>800</td>
      <td>1872</td>
      <td>0</td>
      <td>8</td>
      <td>1248</td>
      <td>0</td>
      <td>0.8</td>
      <td>16</td>
      <td>8</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>274</th>
      <td>376</td>
      <td>8</td>
      <td>0</td>
      <td>880</td>
      <td>2200</td>
      <td>0</td>
      <td>0</td>
      <td>944</td>
      <td>8</td>
      <td>8.0</td>
      <td>8</td>
      <td>8</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>275</th>
      <td>416</td>
      <td>8</td>
      <td>0</td>
      <td>1000</td>
      <td>1696</td>
      <td>0</td>
      <td>8</td>
      <td>1344</td>
      <td>0</td>
      <td>8.0</td>
      <td>16</td>
      <td>16</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>276</th>
      <td>464</td>
      <td>8</td>
      <td>0</td>
      <td>1168</td>
      <td>1744</td>
      <td>0</td>
      <td>8</td>
      <td>840</td>
      <td>0</td>
      <td>16.0</td>
      <td>8</td>
      <td>8</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>277</th>
      <td>456</td>
      <td>8</td>
      <td>8</td>
      <td>992</td>
      <td>2088</td>
      <td>0</td>
      <td>8</td>
      <td>1128</td>
      <td>0</td>
      <td>2.4</td>
      <td>16</td>
      <td>0</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>278</th>
      <td>464</td>
      <td>0</td>
      <td>8</td>
      <td>1088</td>
      <td>2552</td>
      <td>8</td>
      <td>0</td>
      <td>1216</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>279</th>
      <td>488</td>
      <td>8</td>
      <td>0</td>
      <td>1104</td>
      <td>1328</td>
      <td>0</td>
      <td>0</td>
      <td>1000</td>
      <td>8</td>
      <td>28.8</td>
      <td>8</td>
      <td>8</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>280</th>
      <td>336</td>
      <td>8</td>
      <td>0</td>
      <td>1088</td>
      <td>2520</td>
      <td>0</td>
      <td>8</td>
      <td>1000</td>
      <td>8</td>
      <td>14.4</td>
      <td>8</td>
      <td>0</td>
      <td>8</td>
      <td>0</td>
    </tr>
    <tr>
      <th>281</th>
      <td>416</td>
      <td>8</td>
      <td>0</td>
      <td>1024</td>
      <td>1632</td>
      <td>8</td>
      <td>8</td>
      <td>1248</td>
      <td>8</td>
      <td>8.0</td>
      <td>8</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>282</th>
      <td>472</td>
      <td>8</td>
      <td>16</td>
      <td>1008</td>
      <td>1744</td>
      <td>8</td>
      <td>8</td>
      <td>1072</td>
      <td>0</td>
      <td>17.6</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>0</td>
    </tr>
    <tr>
      <th>283</th>
      <td>320</td>
      <td>8</td>
      <td>0</td>
      <td>1216</td>
      <td>1784</td>
      <td>0</td>
      <td>8</td>
      <td>1448</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>0</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>284</th>
      <td>488</td>
      <td>8</td>
      <td>0</td>
      <td>1120</td>
      <td>1656</td>
      <td>0</td>
      <td>0</td>
      <td>1104</td>
      <td>8</td>
      <td>15.2</td>
      <td>16</td>
      <td>8</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>285</th>
      <td>368</td>
      <td>8</td>
      <td>0</td>
      <td>1120</td>
      <td>2488</td>
      <td>0</td>
      <td>8</td>
      <td>960</td>
      <td>8</td>
      <td>14.4</td>
      <td>8</td>
      <td>16</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>286</th>
      <td>472</td>
      <td>8</td>
      <td>24</td>
      <td>1072</td>
      <td>1632</td>
      <td>0</td>
      <td>8</td>
      <td>1296</td>
      <td>0</td>
      <td>6.4</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>287</th>
      <td>456</td>
      <td>8</td>
      <td>8</td>
      <td>1232</td>
      <td>1856</td>
      <td>0</td>
      <td>0</td>
      <td>1312</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>8</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>288</th>
      <td>456</td>
      <td>8</td>
      <td>0</td>
      <td>880</td>
      <td>2680</td>
      <td>0</td>
      <td>8</td>
      <td>1144</td>
      <td>8</td>
      <td>24.0</td>
      <td>8</td>
      <td>8</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>289</th>
      <td>440</td>
      <td>0</td>
      <td>0</td>
      <td>1024</td>
      <td>1640</td>
      <td>0</td>
      <td>16</td>
      <td>1040</td>
      <td>8</td>
      <td>16.0</td>
      <td>8</td>
      <td>8</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>290</th>
      <td>488</td>
      <td>8</td>
      <td>0</td>
      <td>1184</td>
      <td>1624</td>
      <td>0</td>
      <td>8</td>
      <td>1288</td>
      <td>0</td>
      <td>0.0</td>
      <td>16</td>
      <td>8</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>291</th>
      <td>464</td>
      <td>8</td>
      <td>0</td>
      <td>912</td>
      <td>2544</td>
      <td>0</td>
      <td>16</td>
      <td>1120</td>
      <td>0</td>
      <td>35.2</td>
      <td>0</td>
      <td>24</td>
      <td>8</td>
      <td>0</td>
    </tr>
    <tr>
      <th>292</th>
      <td>464</td>
      <td>0</td>
      <td>0</td>
      <td>1360</td>
      <td>1800</td>
      <td>8</td>
      <td>0</td>
      <td>1168</td>
      <td>8</td>
      <td>22.4</td>
      <td>8</td>
      <td>16</td>
      <td>8</td>
      <td>0</td>
    </tr>
    <tr>
      <th>293</th>
      <td>536</td>
      <td>8</td>
      <td>16</td>
      <td>1216</td>
      <td>1696</td>
      <td>0</td>
      <td>0</td>
      <td>1200</td>
      <td>0</td>
      <td>6.4</td>
      <td>8</td>
      <td>0</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>294</th>
      <td>352</td>
      <td>8</td>
      <td>0</td>
      <td>960</td>
      <td>1352</td>
      <td>0</td>
      <td>8</td>
      <td>1152</td>
      <td>8</td>
      <td>22.4</td>
      <td>0</td>
      <td>0</td>
      <td>8</td>
      <td>0</td>
    </tr>
    <tr>
      <th>295</th>
      <td>504</td>
      <td>8</td>
      <td>0</td>
      <td>1120</td>
      <td>1496</td>
      <td>0</td>
      <td>0</td>
      <td>1152</td>
      <td>8</td>
      <td>32.0</td>
      <td>16</td>
      <td>16</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>296</th>
      <td>504</td>
      <td>0</td>
      <td>0</td>
      <td>992</td>
      <td>1576</td>
      <td>0</td>
      <td>8</td>
      <td>1088</td>
      <td>8</td>
      <td>0.0</td>
      <td>8</td>
      <td>0</td>
      <td>16</td>
      <td>0</td>
    </tr>
    <tr>
      <th>297</th>
      <td>472</td>
      <td>8</td>
      <td>0</td>
      <td>1312</td>
      <td>1408</td>
      <td>8</td>
      <td>0</td>
      <td>720</td>
      <td>0</td>
      <td>8.0</td>
      <td>8</td>
      <td>16</td>
      <td>8</td>
      <td>0</td>
    </tr>
    <tr>
      <th>298</th>
      <td>456</td>
      <td>0</td>
      <td>0</td>
      <td>1120</td>
      <td>1928</td>
      <td>0</td>
      <td>8</td>
      <td>984</td>
      <td>8</td>
      <td>1.6</td>
      <td>8</td>
      <td>0</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>299</th>
      <td>360</td>
      <td>8</td>
      <td>24</td>
      <td>880</td>
      <td>2112</td>
      <td>0</td>
      <td>8</td>
      <td>1056</td>
      <td>0</td>
      <td>9.6</td>
      <td>8</td>
      <td>0</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>300</th>
      <td>544</td>
      <td>8</td>
      <td>0</td>
      <td>1152</td>
      <td>1544</td>
      <td>8</td>
      <td>8</td>
      <td>1128</td>
      <td>0</td>
      <td>27.2</td>
      <td>8</td>
      <td>16</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>301</th>
      <td>456</td>
      <td>8</td>
      <td>0</td>
      <td>1040</td>
      <td>1048</td>
      <td>0</td>
      <td>8</td>
      <td>920</td>
      <td>8</td>
      <td>9.6</td>
      <td>8</td>
      <td>8</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>302</th>
      <td>456</td>
      <td>0</td>
      <td>8</td>
      <td>1040</td>
      <td>1888</td>
      <td>0</td>
      <td>0</td>
      <td>1392</td>
      <td>0</td>
      <td>0.0</td>
      <td>8</td>
      <td>8</td>
      <td>16</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>303 rows × 14 columns</p>
</div>




```python
data.head()
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
      <th>age</th>
      <th>sex</th>
      <th>cp</th>
      <th>trestbps</th>
      <th>chol</th>
      <th>fbs</th>
      <th>restecg</th>
      <th>thalach</th>
      <th>exang</th>
      <th>oldpeak</th>
      <th>slope</th>
      <th>ca</th>
      <th>thal</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>63</td>
      <td>1</td>
      <td>3</td>
      <td>145</td>
      <td>233</td>
      <td>1</td>
      <td>0</td>
      <td>150</td>
      <td>0</td>
      <td>2.3</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>37</td>
      <td>1</td>
      <td>2</td>
      <td>130</td>
      <td>250</td>
      <td>0</td>
      <td>1</td>
      <td>187</td>
      <td>0</td>
      <td>3.5</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41</td>
      <td>0</td>
      <td>1</td>
      <td>130</td>
      <td>204</td>
      <td>0</td>
      <td>0</td>
      <td>172</td>
      <td>0</td>
      <td>1.4</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>56</td>
      <td>1</td>
      <td>1</td>
      <td>120</td>
      <td>236</td>
      <td>0</td>
      <td>1</td>
      <td>178</td>
      <td>0</td>
      <td>0.8</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>57</td>
      <td>0</td>
      <td>0</td>
      <td>120</td>
      <td>354</td>
      <td>0</td>
      <td>1</td>
      <td>163</td>
      <td>1</td>
      <td>0.6</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
data[bdata>5]
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
      <th>age</th>
      <th>sex</th>
      <th>cp</th>
      <th>trestbps</th>
      <th>chol</th>
      <th>fbs</th>
      <th>restecg</th>
      <th>thalach</th>
      <th>exang</th>
      <th>oldpeak</th>
      <th>slope</th>
      <th>ca</th>
      <th>thal</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>63</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>145</td>
      <td>233</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>37</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>250</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>187</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>204</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>172</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>56</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>120</td>
      <td>236</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>178</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>120</td>
      <td>354</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>163</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>192</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>148</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>56</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>294</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>153</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>44</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>120</td>
      <td>263</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>173</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>52</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>172</td>
      <td>199</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>162</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>168</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>174</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>10</th>
      <td>54</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>239</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>160</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>48</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>275</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>139</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>12</th>
      <td>49</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>266</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>171</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>64</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>110</td>
      <td>211</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>144</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>283</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>162</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>50</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>120</td>
      <td>219</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>158</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>120</td>
      <td>340</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>172</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>66</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>226</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>114</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>43</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>247</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>171</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>69</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>239</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>151</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>59</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>135</td>
      <td>234</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>161</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>21</th>
      <td>44</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>233</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>179</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22</th>
      <td>42</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>226</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>178</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>23</th>
      <td>61</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>243</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>137</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>24</th>
      <td>40</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>199</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>178</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25</th>
      <td>71</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>160</td>
      <td>302</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>162</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>59</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>212</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>157</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>27</th>
      <td>51</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>110</td>
      <td>175</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>123</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>65</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>417</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>157</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>29</th>
      <td>53</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>197</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>152</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>273</th>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>100</td>
      <td>234</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>156</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>274</th>
      <td>47</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>110</td>
      <td>275</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>118</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>275</th>
      <td>52</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>125</td>
      <td>212</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>168</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>276</th>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>146</td>
      <td>218</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>105</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>277</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>124</td>
      <td>261</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>141</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>278</th>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>136</td>
      <td>319</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>152</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>279</th>
      <td>61</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>138</td>
      <td>166</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>125</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>280</th>
      <td>42</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>136</td>
      <td>315</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>125</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>281</th>
      <td>52</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>128</td>
      <td>204</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>156</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>282</th>
      <td>59</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>126</td>
      <td>218</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>134</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>283</th>
      <td>40</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>152</td>
      <td>223</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>181</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>284</th>
      <td>61</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>207</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>138</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>285</th>
      <td>46</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>311</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>120</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>286</th>
      <td>59</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>134</td>
      <td>204</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>162</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>287</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>154</td>
      <td>232</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>164</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>288</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>110</td>
      <td>335</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>143</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>289</th>
      <td>55</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>128</td>
      <td>205</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>290</th>
      <td>61</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>148</td>
      <td>203</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>161</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>291</th>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>114</td>
      <td>318</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>292</th>
      <td>58</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>170</td>
      <td>225</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>146</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>293</th>
      <td>67</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>152</td>
      <td>212</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>150</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>294</th>
      <td>44</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>120</td>
      <td>169</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>144</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>295</th>
      <td>63</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>187</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>144</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>296</th>
      <td>63</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>124</td>
      <td>197</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>136</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>297</th>
      <td>59</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>164</td>
      <td>176</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>298</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>140</td>
      <td>241</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>123</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>299</th>
      <td>45</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>110</td>
      <td>264</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>132</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>300</th>
      <td>68</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>144</td>
      <td>193</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>141</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>301</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>131</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>115</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>302</th>
      <td>57</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>130</td>
      <td>236</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>174</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>303 rows × 14 columns</p>
</div>




```python
data.iloc[[2,4]]
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
      <th>age</th>
      <th>sex</th>
      <th>cp</th>
      <th>trestbps</th>
      <th>chol</th>
      <th>fbs</th>
      <th>restecg</th>
      <th>thalach</th>
      <th>exang</th>
      <th>oldpeak</th>
      <th>slope</th>
      <th>ca</th>
      <th>thal</th>
      <th>target</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>41</td>
      <td>0</td>
      <td>1</td>
      <td>130</td>
      <td>204</td>
      <td>0</td>
      <td>0</td>
      <td>172</td>
      <td>0</td>
      <td>1.4</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>57</td>
      <td>0</td>
      <td>0</td>
      <td>120</td>
      <td>354</td>
      <td>0</td>
      <td>1</td>
      <td>163</td>
      <td>1</td>
      <td>0.6</td>
      <td>2</td>
      <td>0</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.loc[2:,["age","sex"]].head(10).mean()
```




    age    52.2
    sex     0.6
    dtype: float64




```python
data.loc[::2,::3].tail(9).plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x229fb278390>




![png](http://px6vw3ifw.bkt.clouddn.com/output_10_1.png)



```python
data.loc[0,"age"] = 30
```


```python
data.loc[0,'age']
```




    30






