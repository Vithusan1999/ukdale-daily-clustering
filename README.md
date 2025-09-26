# ukdale-daily-clustering
Machine learning analysis of UK-DALE dataset using unsupervised clustering.  Includes K-Means clustering of daily electricity load profiles, dimensionality reduction with PCA, and cluster interpretation through average daily patterns.

Goal:

Discover recurring daily consumption patterns from smart meter data.

Represent each day as a 24-dimensional vector (average power per hour).

Apply clustering to group similar daily load profiles and evaluate their quality.

Data & Features:

Loads channel_1.dat (timestamp + power) and saves a cleaned channel_1.csv.

Columns created/used: time, power, date, hour, weekday.

Constructs daily_profiles (one row per day, 24 columns for each hour).

Drops incomplete days (NaN rows).

Removes outliers based on 1st and 99th quantiles of total daily consumption.

Saves final feature set as daily_profiles_24h.csv.

Preprocessing / Feature Engineering:

Converts UNIX timestamps → datetime (pd.to_datetime).

Resamples raw 6-second readings to hourly averages.

Pivots to create 24-hour daily profiles.

Standardizes features using StandardScaler.

Clustering:

K-Means (n_clusters=3, n_init=20, random_state=42).

Labels attached back to the daily profiles (cluster).

Plots average daily profile per cluster.

Dimensionality Reduction:

PCA (n_components=2, random_state=42).

Used to visualize clusters in 2D.

Prints explained variance ratio and cumulative variance for first 2 PCs.

Evaluation:

Silhouette Score computed for:

Full scaled 24D space (X_scaled, labels).

PCA-reduced 2D space (X_pca, labels_pca).

Prints cluster sizes and silhouette values.

Visualization:

Line plots of average daily load profile per cluster (hours 0–23).

Scatter plot of clusters in PCA space.

Bar plot of average daily consumption by weekday.

Time-series plots of overall daily averages.

Outputs / Takeaways:

Groups daily load curves into 3 characteristic clusters.

PCA visualization shows clear separation in 2D.

Silhouette scores confirm clustering quality (with and without PCA).

Identifies typical energy use patterns (e.g., consistent, morning-evening peaks).

Saves cleaned datasets (channel_1.csv, daily_profiles_24h.csv) for reuse.
