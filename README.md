# SmartCart Clustering System

## Project Overview
SmartCart Clustering System is a customer-segmentation project that uses machine learning to group customers based on their demographic information and purchasing/spending behavior. The notebook explores customer data, prepares it for analysis, applies clustering algorithms, and summarizes the characteristics of the resulting groups.

## Objectives
- Prepare customer data for machine-learning analysis.
- Create useful features from the available customer information.
- Explore relationships between numerical features.
- Reduce the feature dimensions for visualization and clustering.
- Compare clustering approaches and analyze customer groups.
- Summarize cluster-level income and spending patterns.

## Technologies Used
- **Python** — main programming language
- **Jupyter Notebook** — development and analysis environment
- **Pandas** — data loading and data manipulation
- **Matplotlib** and **Seaborn** — charts and visualizations
- **Scikit-learn** — preprocessing, PCA, K-Means, Agglomerative Clustering, and silhouette scoring
- **kneed** — locating the elbow in the WCSS curve

## Dataset
The notebook expects a CSV file named `smartcart_customers.csv` in the same directory as the notebook.

The analysis uses customer attributes such as income, birth year, customer join date, education, marital status, household children, and spending across product categories. Make sure you have permission to use the dataset and include the CSV locally; it was not included with the uploaded notebook.

## Workflow
1. **Load and inspect data** — read the CSV and check its shape and missing values.
2. **Preprocess data** — fill missing `Income` values with the median.
3. **Feature engineering** — derive `Age`, `Customer_Tenure_Days`, `Total_Spending`, and `Total_Children`.
4. **Simplify categories** — group education levels and marital-status values into broader categories.
5. **Remove columns** — drop identifiers, source columns used to create features, and individual spending columns from the cleaned feature table.
6. **Explore data** — inspect numerical correlations using a heatmap.
7. **Encode categories** — apply one-hot encoding to `Education` and `Living_With`.
8. **Scale features** — use `StandardScaler` to standardize the feature values.
9. **Reduce dimensions** — use PCA to project the scaled data into three components for 3D visualization and clustering.
10. **Choose a cluster count** — examine WCSS with the Elbow Method and calculate silhouette scores.
11. **Cluster customers** — run K-Means and Agglomerative Clustering with four clusters in the current notebook.
12. **Interpret groups** — visualize cluster sizes and income-versus-total-spending patterns, then calculate mean values for each cluster.

## Clustering Methods
- **K-Means:** partitions customers into a specified number of clusters.
- **Agglomerative Clustering:** builds a hierarchy of clusters; the notebook uses Ward linkage and four clusters.
- **PCA (Principal Component Analysis):** reduces the scaled feature space to three components for visualization and clustering.
- **Elbow Method and Silhouette Score:** help examine suitable cluster counts. The final clustering cells currently set the cluster count to `4`.

## Requirements
Install the packages in your Python environment:

```bash
pip install pandas matplotlib seaborn scikit-learn kneed jupyter
```

## How to Run
1. Download or copy the project notebook and the dataset CSV.
2. Put `smartcart_customers.csv` in the same folder as `smartcart(1).ipynb`.
3. Install the required packages.
4. Open a terminal in the project folder and run:

   ```bash
   jupyter notebook
   ```

5. Open the notebook and run the cells from top to bottom.

> Note: The notebook reads the dataset using a relative filename. If the CSV is stored in another folder, update the path in the `pd.read_csv(...)` cell.

## Outputs
When the notebook runs successfully, it produces:
- Data inspection and preprocessing results
- A numerical-feature correlation heatmap
- A 3D PCA scatter plot
- WCSS/Elbow and silhouette-score plots
- 3D cluster visualizations for K-Means and Agglomerative Clustering
- A cluster-count plot
- An income-versus-total-spending scatter plot
- A table of mean feature values for each Agglomerative cluster

## Notes and Limitations
- The notebook's final cluster-characterization section uses the **Agglomerative Clustering** labels.
- The notebook calculates an `optimal_k` with `KneeLocator`, but the final clustering cells explicitly use four clusters.
- The notebook requires `smartcart_customers.csv`; results cannot be reproduced without the expected dataset.
- Cluster numbers are labels, not rankings. Interpret each cluster by reviewing its summary statistics and plots.
- The README describes the current notebook workflow; it does not claim a deployed web application or a production-ready recommendation system.

## Future Improvements
- Add a `requirements.txt` file with tested package versions.
- Save the cluster labels and cluster summary to CSV files.
- Compare both algorithms using consistent evaluation metrics.
- Add clearer names to clusters based on their measured characteristics.
- Validate the pipeline on additional data and document the dataset source.


