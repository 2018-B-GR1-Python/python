# Stacking Arrays

## Concatenate

```python
x = np.array([['Ecuador','Peru'],['Brazil','Venezuela']])
y = np.array([['Uruguay','Bolivia'],['Mexico','Colombia']])
print(x)
print(x.shape)
concatenados_x = np.concatenate((x,y))
print(concatenados_x)
concatenados_y = np.concatenate((x,y), axis = 1)
print(concatenados_y)

```

## Stack

```python
a = np.array([1,2,3])
b = np.array([4,5,6])
c = np.stack((a,b))
print(c)

nombres = ['Adrian','Vicente','Andres','Carlos']
ids = [1,2,3,4]
notas = np.random.rand(4)*100

print(np.stack((nombres,ids,notas)))
print(np.stack((nombres,ids,notas)).shape)
print(np.stack((nombres,ids,notas), axis = 1))
print(np.stack((nombres,ids,notas), axis = 1).shape)
print(np.vstack((nombres,ids,notas)))
print(np.hstack((nombres,ids,notas)))

```




