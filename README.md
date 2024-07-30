# KMeans Algorithm 

KMeans is an iterative clustering algorithm that partitions a dataset into $ K $ distinct non-overlapping clusters. It aims to minimize the variance within each cluster, i.e., it tries to make the intra-cluster points as similar as possible while also keeping the clusters as different as possible.

### Initialization

**K-means++ Initialization**:
1. Choose one centroid randomly from the data points.
2. For each data point $ x $ not chosen yet, compute $ D(x) $, the distance squared from $ x $ to the nearest centroid that has already been chosen.
3. Choose one new data point at random as a new centroid, using a weighted probability distribution where a point $ x $ is chosen with probability proportional to $ D(x)^2 $.
4. Repeat steps 2 and 3 until $ K $ centroids are chosen.

### Algorithm Steps

1. **Assignment Step**:
   $$
   \text{For each point } x_i \text{ in the dataset, assign it to the nearest centroid:}
   $$
   $$
   c^{(i)} = \arg\min_{c_k} \| x_i - c_k \|^2
   $$
   Where $ c^{(i)} $ is the cluster assignment for sample $ i $, $ x_i $ is the feature set of sample $ i $, and $ c_k $ is the centroid for cluster $ k $.

2. **Update Step**:
   $$
   \text{For each cluster } j \text{, recompute the centroid:}
   $$
   $$
   c_k = \frac{1}{|S_k|} \sum_{i \in S_k} x_i
   $$
   Here, $ c_k $ is the new centroid for cluster $ k $, $ S_k $ is the set of all points assigned to cluster $ k $, and $ |S_k| $ is the number of elements in $ S_k $.

### Convergence Criterion

The algorithm iterates between the assignment and update steps until the centroids do not change significantly, determined by a predefined tolerance, or a maximum number of iterations is reached.

### Objective Function

The objective function $ J $ to be minimized is:
$$
J = \sum_{k=1}^K \sum_{x_i \in S_k} \| x_i - c_k \|^2
$$
