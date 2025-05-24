# kmeans-dbscan
Machine Learning KOM A Yunita Sari, S.Kom., M.Sc., Ph.D. Implementing K-Means and DBScan algorithm without libraries
```
Muhammad Argya Vityasy (23/522547/PA/22475)
```

---

This project implements two popular clustering algorithms — **K-Means** and **DBSCAN** — entirely from scratch using only Python's standard libraries (no external ML libraries like scikit-learn).

It is designed for educational purposes to demonstrate the inner workings of clustering algorithms without relying on black-box functions.

## ✨ What’s Implemented

### ✅ K-Means Clustering
- Distance: Euclidean
- Random initialization of centroids
- Convergence check via centroid movement
- Basic point-to-cluster label assignment

### ✅ DBSCAN Clustering
- Uses epsilon (`eps`) and minimum points (`min_pts`) to form clusters
- Detects noise points
- Density-based expansion

---

## 🧪 Sample Results

Both algorithms were tested on synthetic 2D data. Results are printed as cluster labels and visualized using `matplotlib`.

---

## 🔧 Known Issues & Limitations

### K-Means:
- Uses basic **random centroid initialization** → can lead to poor results.
- Not optimized for **duplicate points** or large datasets.
- No support for **distance metric selection** (e.g., Manhattan, cosine).
- No **KMeans++** smart initialization.
- No **automatic choice of `k`**, but we can look at the elbow method to look at the most optimized k value.

### DBSCAN:
- Basic density reachability implementation.
- Uses brute-force distance calculations → not efficient for large datasets.
- Does not use KD-Trees or spatial indexing for optimization.
- No cluster validity metrics (e.g., Silhouette score).

---

## 🚀 How to Run

1. Open the `kmeans_dbscan_nolib.ipynb` Jupyter notebook.
2. Run each cell in sequence.
3. Change input data or parameters (`k`, `eps`, `min_pts`) to experiment with the results.

---

## ✅ Improvements to Consider

If this project were to be extended, the following changes would enhance performance and flexibility:

### For K-Means:
- Use **KMeans++** for better centroid initialization.
- Allow selection of distance metrics.
- Add **data normalization** before clustering.
- Implement **vectorized version** using NumPy for speed.

### For DBSCAN:
- Optimize neighborhood queries using KD-Trees (e.g., with `scipy.spatial.KDTree`).
- Support alternative distance metrics.
- Add visualization of **core**, **border**, and **noise** points.
