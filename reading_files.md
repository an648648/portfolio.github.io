```
# Importing necessary libraries

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Example from Assignment 3 (NESC3505)
```


```
# Subject data 

subjects = ['001_2015_05_22_11_30',
           '002_2015_05_25_14_36',
           '003_2015_05_28_14_09'
           ]

# Example from Assignment 3 (NESC3505)
```


```
# Creating a subdirectory for Python to find the first subject's file path

in_file = subjects[0] + ('/') + subjects[0] + ('_data.txt')
print(in_file)

# Example from Assignment 3 (NESC3505)
```

    001_2015_05_22_11_30/001_2015_05_22_11_30_data.txt



```
# Reading in the first data file

df = pd.read_csv(in_file)

# Example from Assignment 3 (NESC3505)
```
