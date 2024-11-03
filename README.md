# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
#### Step 1: Start 
#### Step 2:Initialization
#### Step 3: Assign data points to clusters
#### Step 4: Update centroids
#### Step 5: Repeat
#### Step 6: Output
#### Step 7: Stop

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Nithilan S
RegisterNumber: 212223240108
*/
```
```py
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:]) 
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred = km.predict(data.iloc[:,3:])
data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="blue", label="cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="green", label="cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="purple", label="cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="orange", label="cluster4")

plt.legend()
plt.title("Customer Segments")
plt.show()
```

## Output:
#### Elbow method:
![image](https://github.com/user-attachments/assets/f4c61ef6-1c1d-4388-ad27-db24f2ccb798)
#### Cluster Segmentation:
![image](https://github.com/user-attachments/assets/c95eec55-e7c0-4018-a6df-5e8a916932d7)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
