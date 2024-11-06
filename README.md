# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Data Preparation: Load data, handle missing values, and extract relevant features for clustering.

2. Determine Clusters: Use the Elbow Method to find optimal number of clusters based on WCSS.

3. K-Means Clustering: Fit the K-Means model with optimal clusters, predict cluster labels for data.

4. Visualization: Plot data points with distinct colors for each cluster to visualize clustering results.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: SARANYA S
RegisterNumber:  212223110044
*/
```
import pandas as pd 
import matplotlib.pyplot as plt 
data=pd.read_csv("Mall_Customers.csv")
data.head()
```
![image](https://github.com/user-attachments/assets/b7aeba18-c48e-43dc-a60f-05d1976987a4)

```
data.info()
```
![image](https://github.com/user-attachments/assets/b162ebdc-e181-4ecb-9c8a-b946f8e474b8)

```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/c8cb291c-ff40-4b9a-a00d-b41c5ebec0ad)

```
from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No.of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
![image](https://github.com/user-attachments/assets/f7259301-6f3f-49b6-a10a-6ccdd1c597e1)

```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
KMeans(n_clusters=5)
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
![image](https://github.com/user-attachments/assets/ef30d5e8-4e32-4021-bf7b-a95e6c4763ae)

```
data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
```
```
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"], color = "gold")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"], color = "orange")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"], color = "green")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"], color = "blue")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"], color = "red")
plt.show()
```
![image](https://github.com/user-attachments/assets/bee24e94-a785-4984-9195-8d413d15a356)

# OUTPUT :
![K Means Clustering for Customer Segmentation](sam.png)


# RESULT :
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
