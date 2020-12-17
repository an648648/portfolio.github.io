## Reading in a csv file

Shared data is usually stored in a csv file so multiple people can access it by specifying its file path. I first had to upload the csv file to cocalc and then I will read it in using pd.read_csv() so that I can manipulate and access its data.


```python
# Importing necessary libraries

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

A list of subjects was created as follows:


```python
subjects = ['001_2015_05_22_11_30',
           '002_2015_05_25_14_36',
           '003_2015_05_28_14_09'
           ]

# Example from Assignment 3 (NESC3505)
```

I am now going to specify a subdirectory, i.e. one value from the list, by accessing its filepath, which has already been loaded. I have chosen to specify the first subject in the above list.


```python
in_file = subjects[0] + ('/') + subjects[0] + ('_data.txt')
print(in_file)

# Example from Assignment 3 (NESC3505)
```

    001_2015_05_22_11_30/001_2015_05_22_11_30_data.txt


Now I can read in the first file using pd.read_csv().


```python
df = pd.read_csv(in_file)

# Example from Assignment 3 (NESC3505)
```

The dataframe is now loaded and ready to go!


```python

```
