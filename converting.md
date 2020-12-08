```python
# Converting x in seconds to miliseconds, in the 'rt' column of dataframe df

def conversion (x):
    return x * 1000
df['rt'] = df['rt'].apply(conversion)

# Example from Assignment 3 (NESC3505)
```


```python
# Transforming z to an inverse function of column 'rt' in dataframe df

def transform (z):
    return 1/r
df['invert'] = df['rt'].apply(transform)

# Example from Assignment 3 (NESC3505)
```


```python
# Using if/else statements to manipulate data

x = 4
if x **2 == 16:
    print('x is correct')
else:
    print('x is false')

# Example of if/else statements as I learned in DataCamp lessons
```
