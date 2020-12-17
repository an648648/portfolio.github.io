## Basic functions 

A common function in neural data science is to convert values from seconds to milliseconds so that values are easier to read and manipulate. Basically, any mathematical functions can be used to change data! In this example, I willcreate a multiplication function and an inverse function.

I will also show how to create an if-elif-else statement which is used to execute a statement or multiple statements. I split the age groups, from the dataframe defined below, into multiple subcategories. This could be a useful visualizing tool for large groups of people so that you know who is in what age group!


```python
import pandas as pd
```

I will be working with dataframe 'df', which contains all data from the 'oasis_cross-sectional' csv file.


```python
df = pd.read_csv('oasis_cross-sectional.csv')
```


```python
df
```





<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>M/F</th>
      <th>Hand</th>
      <th>Age</th>
      <th>Educ</th>
      <th>SES</th>
      <th>MMSE</th>
      <th>CDR</th>
      <th>eTIV</th>
      <th>nWBV</th>
      <th>ASF</th>
      <th>Delay</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>OAS1_0001_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>74</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>29.0</td>
      <td>0.0</td>
      <td>1344</td>
      <td>0.743</td>
      <td>1.306</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OAS1_0002_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>55</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>29.0</td>
      <td>0.0</td>
      <td>1147</td>
      <td>0.810</td>
      <td>1.531</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>OAS1_0003_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>73</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>27.0</td>
      <td>0.5</td>
      <td>1454</td>
      <td>0.708</td>
      <td>1.207</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OAS1_0004_MR1</td>
      <td>M</td>
      <td>R</td>
      <td>28</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1588</td>
      <td>0.803</td>
      <td>1.105</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OAS1_0005_MR1</td>
      <td>M</td>
      <td>R</td>
      <td>18</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1737</td>
      <td>0.848</td>
      <td>1.010</td>
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
    </tr>
    <tr>
      <th>431</th>
      <td>OAS1_0285_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>20</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1469</td>
      <td>0.847</td>
      <td>1.195</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>432</th>
      <td>OAS1_0353_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1684</td>
      <td>0.790</td>
      <td>1.042</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>433</th>
      <td>OAS1_0368_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1580</td>
      <td>0.856</td>
      <td>1.111</td>
      <td>89.0</td>
    </tr>
    <tr>
      <th>434</th>
      <td>OAS1_0379_MR2</td>
      <td>F</td>
      <td>R</td>
      <td>20</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1262</td>
      <td>0.861</td>
      <td>1.390</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>435</th>
      <td>OAS1_0395_MR2</td>
      <td>F</td>
      <td>R</td>
      <td>26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1283</td>
      <td>0.834</td>
      <td>1.368</td>
      <td>39.0</td>
    </tr>
  </tbody>
</table>
<p>436 rows × 12 columns</p>
</div>



The nWBV column would be much easier to read in whole numbers, rather than decimals. The following function will convert each decimal to a whole number.


```python
def convert_to_whole (x):
    return x * 1000
df['nWBV'] = df['nWBV'].apply(convert_to_whole)

df
```





<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>M/F</th>
      <th>Hand</th>
      <th>Age</th>
      <th>Educ</th>
      <th>SES</th>
      <th>MMSE</th>
      <th>CDR</th>
      <th>eTIV</th>
      <th>nWBV</th>
      <th>ASF</th>
      <th>Delay</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>OAS1_0001_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>74</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>29.0</td>
      <td>0.0</td>
      <td>1344</td>
      <td>743.0</td>
      <td>1.306</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OAS1_0002_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>55</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>29.0</td>
      <td>0.0</td>
      <td>1147</td>
      <td>810.0</td>
      <td>1.531</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>OAS1_0003_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>73</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>27.0</td>
      <td>0.5</td>
      <td>1454</td>
      <td>708.0</td>
      <td>1.207</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OAS1_0004_MR1</td>
      <td>M</td>
      <td>R</td>
      <td>28</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1588</td>
      <td>803.0</td>
      <td>1.105</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OAS1_0005_MR1</td>
      <td>M</td>
      <td>R</td>
      <td>18</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1737</td>
      <td>848.0</td>
      <td>1.010</td>
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
    </tr>
    <tr>
      <th>431</th>
      <td>OAS1_0285_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>20</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1469</td>
      <td>847.0</td>
      <td>1.195</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>432</th>
      <td>OAS1_0353_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1684</td>
      <td>790.0</td>
      <td>1.042</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>433</th>
      <td>OAS1_0368_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1580</td>
      <td>856.0</td>
      <td>1.111</td>
      <td>89.0</td>
    </tr>
    <tr>
      <th>434</th>
      <td>OAS1_0379_MR2</td>
      <td>F</td>
      <td>R</td>
      <td>20</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1262</td>
      <td>861.0</td>
      <td>1.390</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>435</th>
      <td>OAS1_0395_MR2</td>
      <td>F</td>
      <td>R</td>
      <td>26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1283</td>
      <td>834.0</td>
      <td>1.368</td>
      <td>39.0</td>
    </tr>
  </tbody>
</table>
<p>436 rows × 12 columns</p>
</div>



This is now much easier to work with than when nWBV was in decimals!

I can also transform multiple columns using the same function. In the following example, I take the inverse of all data in columns nWBV and ASF using only one function. Once a function is defined, it can be applied to anything!


```python
def transform (z):
    return 1/z
df['invert'] = df['nWBV'].apply(transform)
df['invert2'] = df['ASF'].apply(transform)
df
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
      <th>ID</th>
      <th>M/F</th>
      <th>Hand</th>
      <th>Age</th>
      <th>Educ</th>
      <th>SES</th>
      <th>MMSE</th>
      <th>CDR</th>
      <th>eTIV</th>
      <th>nWBV</th>
      <th>ASF</th>
      <th>Delay</th>
      <th>invert</th>
      <th>invert2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>OAS1_0001_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>74</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>29.0</td>
      <td>0.0</td>
      <td>1344</td>
      <td>743.0</td>
      <td>1.306</td>
      <td>NaN</td>
      <td>0.001346</td>
      <td>0.765697</td>
    </tr>
    <tr>
      <th>1</th>
      <td>OAS1_0002_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>55</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>29.0</td>
      <td>0.0</td>
      <td>1147</td>
      <td>810.0</td>
      <td>1.531</td>
      <td>NaN</td>
      <td>0.001235</td>
      <td>0.653168</td>
    </tr>
    <tr>
      <th>2</th>
      <td>OAS1_0003_MR1</td>
      <td>F</td>
      <td>R</td>
      <td>73</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>27.0</td>
      <td>0.5</td>
      <td>1454</td>
      <td>708.0</td>
      <td>1.207</td>
      <td>NaN</td>
      <td>0.001412</td>
      <td>0.828500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OAS1_0004_MR1</td>
      <td>M</td>
      <td>R</td>
      <td>28</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1588</td>
      <td>803.0</td>
      <td>1.105</td>
      <td>NaN</td>
      <td>0.001245</td>
      <td>0.904977</td>
    </tr>
    <tr>
      <th>4</th>
      <td>OAS1_0005_MR1</td>
      <td>M</td>
      <td>R</td>
      <td>18</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1737</td>
      <td>848.0</td>
      <td>1.010</td>
      <td>NaN</td>
      <td>0.001179</td>
      <td>0.990099</td>
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
      <th>431</th>
      <td>OAS1_0285_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>20</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1469</td>
      <td>847.0</td>
      <td>1.195</td>
      <td>2.0</td>
      <td>0.001181</td>
      <td>0.836820</td>
    </tr>
    <tr>
      <th>432</th>
      <td>OAS1_0353_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1684</td>
      <td>790.0</td>
      <td>1.042</td>
      <td>40.0</td>
      <td>0.001266</td>
      <td>0.959693</td>
    </tr>
    <tr>
      <th>433</th>
      <td>OAS1_0368_MR2</td>
      <td>M</td>
      <td>R</td>
      <td>22</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1580</td>
      <td>856.0</td>
      <td>1.111</td>
      <td>89.0</td>
      <td>0.001168</td>
      <td>0.900090</td>
    </tr>
    <tr>
      <th>434</th>
      <td>OAS1_0379_MR2</td>
      <td>F</td>
      <td>R</td>
      <td>20</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1262</td>
      <td>861.0</td>
      <td>1.390</td>
      <td>2.0</td>
      <td>0.001161</td>
      <td>0.719424</td>
    </tr>
    <tr>
      <th>435</th>
      <td>OAS1_0395_MR2</td>
      <td>F</td>
      <td>R</td>
      <td>26</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1283</td>
      <td>834.0</td>
      <td>1.368</td>
      <td>39.0</td>
      <td>0.001199</td>
      <td>0.730994</td>
    </tr>
  </tbody>
</table>
<p>436 rows × 14 columns</p>
</div>



Finally, to split the age column into 3 categories, I can use an if-elif-else statement. This function looks over the data to determine which parts agree with the if statement, and returns whatever I choose in brackets. Next, the function looks over the data using the elif statement to determine which parts agree with it, then returns whatever I choose to put in brackets just below the elif statement. Lastly, the function looks over the else statement. In my else statement, I want the function to return the rest of the data as ('32 or older') so that all participants are accounted for in my new age categories


```python
def split_age_groups (age):
    if age <= 25:
        return('less than 26')
    elif age > 25 and age < 32:
        return('25-32')
    else:
        return('32 or older')

df['age group'] = df['Age'].apply(split_age_groups)
df[['age group']]
```





<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>age group</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>32 or older</td>
    </tr>
    <tr>
      <th>1</th>
      <td>32 or older</td>
    </tr>
    <tr>
      <th>2</th>
      <td>32 or older</td>
    </tr>
    <tr>
      <th>3</th>
      <td>25-32</td>
    </tr>
    <tr>
      <th>4</th>
      <td>less than 26</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>431</th>
      <td>less than 26</td>
    </tr>
    <tr>
      <th>432</th>
      <td>less than 26</td>
    </tr>
    <tr>
      <th>433</th>
      <td>less than 26</td>
    </tr>
    <tr>
      <th>434</th>
      <td>less than 26</td>
    </tr>
    <tr>
      <th>435</th>
      <td>25-32</td>
    </tr>
  </tbody>
</table>
<p>436 rows × 1 columns</p>
</div>


