# Machine Learning: K-Means and DBSCAN Implementation from Scratch

**Name:** Muhammad Argya Vityasy (23/522547/PA/22475)  
**Course:** Machine Learning KOM A  
**Instructor:** Yunita Sari, S.Kom., M.Sc., Ph.D.

---

## Introduction

Clustering is a fundamental unsupervised machine learning technique that groups similar data points together without prior knowledge of the group labels. This project implements two prominent clustering algorithms—**K-Means** and **DBSCAN**—entirely from scratch using only Python's standard libraries, without relying on external machine learning frameworks like scikit-learn.

### Objectives

The primary objectives of this implementation are:

1. **Educational Understanding**: Demonstrate the mathematical foundations and algorithmic steps of clustering algorithms
2. **Algorithm Comparison**: Compare the performance and characteristics of centroid-based (K-Means) versus density-based (DBSCAN) clustering approaches
3. **Parameter Analysis**: Investigate the impact of hyperparameters on clustering quality and performance
4. **Practical Implementation**: Provide a clear, readable implementation that can serve as a learning resource

### Dataset

The implementation uses the classic **Iris dataset** from the UCI Machine Learning Repository, which contains 150 samples of iris flowers with four features (sepal length, sepal width, petal length, petal width) across three species. For visualization purposes, the analysis focuses on the first two dimensions (sepal length and sepal width).

---

## Methodology

### K-Means Algorithm Implementation

K-Means is a centroid-based clustering algorithm that partitions data into k clusters by minimizing within-cluster sum of squares (WCSS).

#### Algorithm Steps:
1. **Initialization**: Randomly select k centroids from the dataset
2. **Assignment**: Assign each data point to the nearest centroid using Euclidean distance
3. **Update**: Recalculate centroids as the mean of assigned points
4. **Convergence**: Repeat steps 2-3 until centroids move less than a specified tolerance or maximum iterations reached

#### Key Implementation Details:
- **Distance Metric**: Euclidean distance calculation
- **Convergence Criteria**: Tolerance-based centroid movement (1e-4)
- **Empty Cluster Handling**: Re-initialization with random data points
- **Reproducibility**: Optional random seed parameter

#### Optimal k Selection - Elbow Method:
The elbow method evaluates WCSS for different k values (1-10) to identify the optimal number of clusters. The "elbow point" indicates where additional clusters provide diminishing returns in WCSS reduction.

### DBSCAN Algorithm Implementation

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) is a density-based algorithm that groups together points in high-density areas while marking isolated points as noise.

#### Algorithm Steps:
1. **Core Point Identification**: Points with at least `min_pts` neighbors within `eps` radius
2. **Cluster Formation**: Expand clusters from core points by including density-reachable points
3. **Border Point Assignment**: Non-core points within `eps` of core points join the cluster
4. **Noise Detection**: Points that don't meet core or border criteria are marked as noise (-1)

#### Key Implementation Details:
- **Neighborhood Query**: Brute-force distance calculation for neighbor identification
- **Cluster Expansion**: Breadth-first expansion from core points
- **Noise Handling**: Explicit noise point labeling and visualization
- **Parameter Sensitivity**: Systematic evaluation of `eps` and `min_pts` combinations

---

## Results and Analysis

### K-Means Clustering Results

#### Elbow Method Analysis:
The elbow plot revealed that k=3 provides the optimal balance between cluster cohesion and model complexity, aligning with the known three species in the Iris dataset. The WCSS values showed:
- Steep decrease from k=1 to k=3
- Gradual decline after k=3, indicating diminishing returns
- Clear elbow at k=3, suggesting natural grouping structure

#### Clustering Performance:
With k=3, the K-Means algorithm successfully identified three distinct clusters corresponding to the iris species, with centroids clearly positioned at the cluster centers.

### DBSCAN Parameter Tuning Results

Systematic evaluation of parameter combinations revealed:

#### Epsilon (eps) Impact:
- **eps = 0.3-0.4**: Very tight clusters, potential over-segmentation
- **eps = 0.5-0.6**: Balanced clustering with reasonable noise detection
- **eps = 0.7+**: Risk of merging distinct clusters

#### Minimum Points (min_pts) Impact:
- **min_pts = 2-3**: Less robust to noise, more clusters formed
- **min_pts = 4-6**: Balanced density requirement
- **min_pts = 7+**: Stricter density criteria, more noise points

#### Optimal Parameters:
The combination of **eps=0.6** and **min_pts=5** provided the most interpretable results, producing distinct clusters while maintaining reasonable noise detection.

## Study Limitations and Considerations

### K-Means Limitations:
1. **Initialization Sensitivity**: Random centroid initialization can lead to suboptimal solutions
2. **Spherical Assumption**: Assumes clusters are spherical and similar-sized
3. **Fixed k Requirement**: Requires prior specification of cluster number
4. **Outlier Sensitivity**: Sensitive to outliers affecting centroid positions

### DBSCAN Limitations:
1. **Parameter Sensitivity**: Performance heavily dependent on eps and min_pts selection
2. **Varying Density**: Struggles with clusters of varying densities
3. **Computational Complexity**: O(n²) implementation without spatial indexing
4. **High-Dimensional Challenges**: Distance-based metrics suffer in high dimensions

### Implementation Considerations:
- **No Advanced Optimization**: Basic implementations without KMeans++ or spatial indexing
- **Limited Distance Metrics**: Only Euclidean distance implemented
- **Visualization Constraints**: 2D visualization limits comprehensive analysis
- **Dataset Scale**: Tested on small dataset (150 samples)

---

## Conclusion

This project successfully demonstrates the implementation and analysis of two fundamental clustering algorithms from scratch. The educational value lies in understanding the algorithmic mechanics without the abstraction of high-level libraries.

### Key Findings:

1. **Algorithm Complementarity**: K-Means and DBSCAN serve different clustering scenarios—K-Means for well-separated, spherical clusters, and DBSCAN for arbitrary shapes with noise handling

2. **Parameter Criticality**: Both algorithms require careful parameter tuning, with DBSCAN being particularly sensitive to eps and min_pts selection

3. **Implementation Insights**: Building algorithms from scratch reveals computational trade-offs and design decisions typically hidden in library implementations

4. **Practical Applications**: The elbow method provides a systematic approach for K-Means parameter selection, while DBSCAN's parameter grid search enables comprehensive evaluation
