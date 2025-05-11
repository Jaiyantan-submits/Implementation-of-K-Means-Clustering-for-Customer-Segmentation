# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Load and preprocess data: Import data, inspect it, and handle missing values if any.
2. Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.
3. Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features.
4. Assign cluster labels to each data point.
5. Plot data points in a scatter plot, color-coded by cluster assignments for interpretation.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: JAIYANTAN S
RegisterNumber: 212224100021
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters=5, n_init=10)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster5")
plt.legend()
plt.title("Customer Segments")


```



## Output:

![image](https://github.com/user-attachments/assets/8d20cbf1-7f4b-40c4-873a-d3d36096004a)

![image](https://github.com/user-attachments/assets/c5e8215f-3f7a-4fbd-a7e1-85e5b3b6ca56)

![image](https://github.com/user-attachments/assets/100312a9-b0ea-4a9c-93cb-67e6be4e5274)

![image](https://github.com/user-attachments/assets/51fdcb17-f23b-45f0-85c4-d5bc71f8910d)

![image](https://github.com/user-attachments/assets/4629981c-f341-49bb-b664-aa5dd0e99b31)

![image](https://github.com/user-attachments/assets/e0b052b1-f278-43b9-8581-2db5d8c11d08)

![image](https://github.com/user-attachments/assets/67ad20ea-d304-45ad-ba2f-a5431b6230aa)

![image](https://github.com/user-attachments/assets/b1215dbe-85da-4411-a6c2-f25256280baf)

![image](https://github.com/user-attachments/assets/24f1b3b8-9158-442f-a9fa-246235856c0a)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
