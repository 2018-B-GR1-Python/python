# Bar plots and Histograms 


```python
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline
plt.rcParams['figure.figsize'] = (4,3)
plt.rcParams['figure.dpi'] = 150

# Basic Plot
nums = np.random.uniform(size=10)
plt.bar(np.arange(10),height=nums)

# Horizontal Plot
plt.barh(np.arange(10), width=nums) # No olvidar de cambiar height por width

# Colores y edge color
# No olvidar de cambiar height por width
plt.barh(np.arange(10), width=nums, color='limegreen', edgecolor='maroon') # los edgecolor y color pueden valer none

# Alineacion
plt.bar(np.arange(10), nums, align='center')  # edge

# hatch & fill
plt.bar(np.arange(10), nums, hatch='-')

plt.bar(np.arange(10), nums, hatch='x', color='none', edgecolor='maroon')

# Width de la barra 1 > 0 
plt.bar(np.arange(10), nums, width=0.5) # 1 0.1 2 

# Width de la barra 1 > 0 
plt.bar(np.arange(10), nums, bottom=0.1*nums) # Tamano del espacio en el bottom

# Histogramas (distribucion normal)

# basic
rands = np.random.normal(size=int(1e6))
plt.hist(rands)

# Valores del histograma
print(plt.hist(rands))
plt.clf()

# Rango (solo valores positivos por ejemplo)
plt.hist(rands, range=(0,4))  # 4 3 2 1 0.5


# Bin
plt.hist(rands, bins='auto', histtype='stepfilled')  # [0,1,2,3,4,5,6,7]

# Acumulativo
plt.hist(rands, bins='auto', cumulative=True)  # -1

# Multiples
plt.hist((rands, 0.5*rands), bins='auto', histtype='stepfilled') 




```
