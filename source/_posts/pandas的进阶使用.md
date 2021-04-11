---
title: pandas的进阶使用
date: 2021-04-11 15:52:34
categroies:
  - python
tags:
  - 数据分析
  - 数据处理
---

```python
import pandas as pd
import numpy as np

data = np.random.randn(4,5)
data_frame = pd.DataFrame(data,columns=list("ABCDE"))
```

<!--more-->

```python
data
```

    array([[ 8.25634519e-01, -9.25905820e-01,  1.60605347e-01,
             4.59769960e-01, -5.53728862e-01],
           [-1.05283115e+00, -1.39125624e+00, -1.12922912e+00,
             1.49767697e+00,  5.35233430e-04],
           [ 2.53482903e-01,  5.47140132e-01, -2.06516385e-01,
            -4.47969335e-01,  1.67777462e+00],
           [ 1.88872120e-01, -2.44798093e+00, -1.90417219e-01,
             9.94792750e-01, -1.35500775e+00]])

```python
data_frame
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
      <td>0.825635</td>
      <td>-0.925906</td>
      <td>0.160605</td>
      <td>0.459770</td>
      <td>-0.553729</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-1.052831</td>
      <td>-1.391256</td>
      <td>-1.129229</td>
      <td>1.497677</td>
      <td>0.000535</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.253483</td>
      <td>0.547140</td>
      <td>-0.206516</td>
      <td>-0.447969</td>
      <td>1.677775</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.188872</td>
      <td>-2.447981</td>
      <td>-0.190417</td>
      <td>0.994793</td>
      <td>-1.355008</td>
    </tr>
  </tbody>
</table>
</div>

1 求每一列的出现的次数、平均值、标准差、最小值、最大值和分位数

```python
data_frame.describe()
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
      <th>count</th>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
      <td>4.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.053790</td>
      <td>-1.054501</td>
      <td>-0.341389</td>
      <td>0.626068</td>
      <td>-0.057607</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.791302</td>
      <td>1.243246</td>
      <td>0.551868</td>
      <td>0.832040</td>
      <td>1.283785</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-1.052831</td>
      <td>-2.447981</td>
      <td>-1.129229</td>
      <td>-0.447969</td>
      <td>-1.355008</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>-0.121554</td>
      <td>-1.655437</td>
      <td>-0.437195</td>
      <td>0.232835</td>
      <td>-0.754049</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.221178</td>
      <td>-1.158581</td>
      <td>-0.198467</td>
      <td>0.727281</td>
      <td>-0.276597</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.396521</td>
      <td>-0.557644</td>
      <td>-0.102662</td>
      <td>1.120514</td>
      <td>0.419845</td>
    </tr>
    <tr>
      <th>max</th>
      <td>0.825635</td>
      <td>0.547140</td>
      <td>0.160605</td>
      <td>1.497677</td>
      <td>1.677775</td>
    </tr>
  </tbody>
</table>
</div>

2 求某一列的平均值

```python
data_frame["A"].mean()
```

    0.053789598692845664

3 求和

```python
data_frame.sum(axis=0)
```

    A    0.215158
    B   -4.218003
    C   -1.365557
    D    2.504270
    E   -0.230427
    dtype: float64

4 条件筛选

```python
data_frame>0
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
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>

```python
data_frame[data_frame>0]
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
      <td>0.825635</td>
      <td>NaN</td>
      <td>0.160605</td>
      <td>0.459770</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.497677</td>
      <td>0.000535</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.253483</td>
      <td>0.54714</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1.677775</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.188872</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.994793</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>

```python
data_frame[data_frame["A"]>0]
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
      <td>0.825635</td>
      <td>-0.925906</td>
      <td>0.160605</td>
      <td>0.459770</td>
      <td>-0.553729</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.253483</td>
      <td>0.547140</td>
      <td>-0.206516</td>
      <td>-0.447969</td>
      <td>1.677775</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.188872</td>
      <td>-2.447981</td>
      <td>-0.190417</td>
      <td>0.994793</td>
      <td>-1.355008</td>
    </tr>
  </tbody>
</table>
</div>

```python
data_frame[(data_frame["A"]>0) & (data_frame["B"]<0)]
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
      <td>0.825635</td>
      <td>-0.925906</td>
      <td>0.160605</td>
      <td>0.459770</td>
      <td>-0.553729</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.188872</td>
      <td>-2.447981</td>
      <td>-0.190417</td>
      <td>0.994793</td>
      <td>-1.355008</td>
    </tr>
  </tbody>
</table>
</div>

5 排序

```python
data_frame.sort_values(by=["A","B"],ascending=[True,False])
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
      <th>1</th>
      <td>-1.052831</td>
      <td>-1.391256</td>
      <td>-1.129229</td>
      <td>1.497677</td>
      <td>0.000535</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.188872</td>
      <td>-2.447981</td>
      <td>-0.190417</td>
      <td>0.994793</td>
      <td>-1.355008</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.253483</td>
      <td>0.547140</td>
      <td>-0.206516</td>
      <td>-0.447969</td>
      <td>1.677775</td>
    </tr>
    <tr>
      <th>0</th>
      <td>0.825635</td>
      <td>-0.925906</td>
      <td>0.160605</td>
      <td>0.459770</td>
      <td>-0.553729</td>
    </tr>
  </tbody>
</table>
</div>

6 高级应用 apply 和 applymap

```python
data_frame.apply(lambda row: row**2)
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
      <td>0.681672</td>
      <td>0.857302</td>
      <td>0.025794</td>
      <td>0.211388</td>
      <td>3.066157e-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.108453</td>
      <td>1.935594</td>
      <td>1.275158</td>
      <td>2.243036</td>
      <td>2.864748e-07</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.064254</td>
      <td>0.299362</td>
      <td>0.042649</td>
      <td>0.200677</td>
      <td>2.814928e+00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.035673</td>
      <td>5.992611</td>
      <td>0.036259</td>
      <td>0.989613</td>
      <td>1.836046e+00</td>
    </tr>
  </tbody>
</table>
</div>

```python
data_frame.apply(lambda row: row>0)
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
      <td>True</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>True</td>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>True</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>

```python
def replace(i):
    if i< 0:
        return 0
    else:
        return i**2
data_frame.applymap(replace)
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
      <td>0.681672</td>
      <td>0.000000</td>
      <td>0.025794</td>
      <td>0.211388</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.243036</td>
      <td>2.864748e-07</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.064254</td>
      <td>0.299362</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.814928e+00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.035673</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.989613</td>
      <td>0.000000e+00</td>
    </tr>
  </tbody>
</table>
</div>

7 透视表 pivot 函数第一个参数表示行索引，第二个参数表示列索引，第三个参数表示要显示的值

```python
data_frame.pivot("A","B","C")
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
      <th>B</th>
      <th>-2.447981</th>
      <th>-1.391256</th>
      <th>-0.925906</th>
      <th>0.547140</th>
    </tr>
    <tr>
      <th>A</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>-1.052831</th>
      <td>NaN</td>
      <td>-1.129229</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.188872</th>
      <td>-0.190417</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.253483</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>-0.206516</td>
    </tr>
    <tr>
      <th>0.825635</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.160605</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
