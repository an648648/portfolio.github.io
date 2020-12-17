## 3D Slicing through MRI images


```python
import imageio
import scipy.ndimage as ndi
import scipy.stats
import nibabel as nib
import numpy as np
import matplotlib.pyplot as plt
```

The data we are working with is a large set  (160) of DICOM files, each containing an image of a slice through the brain. To load the dataset, instead of using pd.read_csv, we use imageio.volread.


```python
vol = imageio.volread('5.T1_GRE_3D_AXIAL')
```

    Reading DICOM (examining files): 1/161 files (0.6%)161/161 files (100.0%)
      Found 1 correct series.
    Reading DICOM (loading data): 160/160  (100.0%)


This is the middle slice of the brain image:


```python
plt.imshow(vol[79])
plt.show()
```




    
![png](mri_files/mri_5_0.png)
    



In order to view multiple slices of the the brain, every 10th slice of 160 slices is plotted. Therefore, a 4 x 4 array of suplots (i.e. images of slices) is generated.


```python
fig = plt.figure(figsize=[8, 12])
subplot_counter = 1

for ii in range (0, 160, 10):
    fig.add_subplot(4,4, subplot_counter)
    plt.imshow(vol[ii], cmap = 'gray')
    plt.axis('off')
    plt.tight_layout()
    subplot_counter += 1
    
plt.show()
```




    
![png](mri_files/mri_7_0.png)
    



The data and code is from Assignment 5 in NESC3505, Dalhousie University. I developed this code with the help of my classmates: Jill Fennell, Jocelyn Morrison, Paul Jean and Retage Al-Bader


```python

```
