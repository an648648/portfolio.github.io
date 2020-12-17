## Raster Plots

Raster plots are an effective way to visualize action potential frequency from a single cell over time. The x-axis represents time and the y-axis is the action potential. Each spike will be exactly 1 on the y-axis because action potentials are discrete and countable and are either present or absent. The following code will show how to graph a raster project for a cell from the 'crowder_1_neuron' DataFrame. This data was obtained from Assignment 4 in NESC3505, Dalhousie University.


```
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
```


```
df = pd.read_csv('crowder_1_neuron.csv')
```


```
df
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>neuron</th>
      <th>time</th>
      <th>repetition</th>
      <th>contrast</th>
      <th>condition</th>
      <th>spike</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>m6_11</td>
      <td>0</td>
      <td>1</td>
      <td>4</td>
      <td>CTRL</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>m6_11</td>
      <td>1</td>
      <td>1</td>
      <td>4</td>
      <td>CTRL</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>m6_11</td>
      <td>2</td>
      <td>1</td>
      <td>4</td>
      <td>CTRL</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>m6_11</td>
      <td>3</td>
      <td>1</td>
      <td>4</td>
      <td>CTRL</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>m6_11</td>
      <td>4</td>
      <td>1</td>
      <td>4</td>
      <td>CTRL</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>639995</th>
      <td>m6_11</td>
      <td>3995</td>
      <td>8</td>
      <td>100</td>
      <td>ADAPT</td>
      <td>0</td>
    </tr>
    <tr>
      <th>639996</th>
      <td>m6_11</td>
      <td>3996</td>
      <td>8</td>
      <td>100</td>
      <td>ADAPT</td>
      <td>0</td>
    </tr>
    <tr>
      <th>639997</th>
      <td>m6_11</td>
      <td>3997</td>
      <td>8</td>
      <td>100</td>
      <td>ADAPT</td>
      <td>0</td>
    </tr>
    <tr>
      <th>639998</th>
      <td>m6_11</td>
      <td>3998</td>
      <td>8</td>
      <td>100</td>
      <td>ADAPT</td>
      <td>0</td>
    </tr>
    <tr>
      <th>639999</th>
      <td>m6_11</td>
      <td>3999</td>
      <td>8</td>
      <td>100</td>
      <td>ADAPT</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>640000 rows × 6 columns</p>



To create a Raster plot, I first must subset the data for only one trial, condition and contrast level. 

In Assignment 4, I chose the first trial, the highest contrast level(100) and the control condition. I also selected only the values where spike = 1 as the Raster plot displays the times at which an action potential is elicited.


```
df[(df['repetition'] == 1) & (df['contrast'] == 100) & (df['condition'] == 'CTRL') & (df['spike'] == 1)]
```

To create the plot, the same code is required with the additional ['time'] column at the end of the code. I set it equal to spike_times so I could plot the Raster plot using plt.vlines()


```
spike_times = df[(df['repetition'] == 1) & (df['contrast'] == 100) & (df['condition'] == 'CTRL') & (df['spike'] == 1)]['time']

fig = plt.figure()
plt.vlines(spike_times, 0, 1);
```




    
![png]c.png)
    



I collaborated on this code with fellow classmates: Jill Fennell, Jocelyn Morrison, Paul Jean and Retage Al-Bader


```

```
