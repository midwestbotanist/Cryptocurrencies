# Cryptocurrencies

## Background and Purpose:
During the Covid19 pandemic, cryptocurrencies entered the limelight as Bitcoin's worth reached up to $65k per coin at its peak in 2021. Though it just recently became so well known to the public, cryptocurrencies first began in the ideas of B-Money and Bit Gold between 1998-2009 (neither of these coins reached full development). Since Bitcoin first started to be traded in 2011, it has been the most well-known coin on the market with multiple fluctuations over time (as of January 2023, the current price is ~$20k per coin)[1].

Due to the increased public interest in cryptocurrencies, many traditional investing institutions have expanded there repertoire to include crypto options. Accountability Accounting, like many other traditional institutions, is an investment bank interested in expanding their portfolio options to include crypto. As it is new to them, Accountability Accounting has requested a report covering available coins on the market along with a classification system to group them by.

Unsupervised learning has been selected due to there being no expected output. The cryptocurrencies are being grouped through a clustering algorithm, and data visualizations will be generated. 

## Preprocessing Data for PCA:
### Initial DataFrame generated after csv import:
![crypto_data_preCleaned](https://user-images.githubusercontent.com/101941048/212574094-c5f37ad5-5e41-4ba7-9250-20f397948ba7.png)

### CoinNames split into Separate DataFrame (due to CoinNames not being used in the clustering algorithm):
![crypto_names_only](https://user-images.githubusercontent.com/101941048/212573673-59aaf599-372a-4500-aedb-d83d942e287e.png)

### The renaming crypto_df DataFrame after removing the null values, keeping only coins being traded, and CoinName removed:
![crypto_df](https://user-images.githubusercontent.com/101941048/212573633-f422fa3d-3520-494a-9faf-af7488eb374b.png)

".get_dummies()" is used to convert categorical data into dummy/indicator values for the "Algorithm" and "ProofType" text features, from which the features are further standardized using "StandardScaler().fit_transform()".

## Data Dimension Reduction Using PCA:
### Principal Component Analysis (PCA) Algorithm Reducing Dimensions to 3 Principal Components:
![pca_df](https://user-images.githubusercontent.com/101941048/212573727-4418d98b-15fb-4773-8422-c6de7e2362d9.png)

Using the data cleaned during preprocessing, the PCA algorithm was utilized here to reduce down to 3 principal components which will then be used with the K-means clustering.

## K-means for Cryptocurrency Clustering:
### Elbow Curve resulting from PCA DataFrame from Above:
![elbow_data](https://user-images.githubusercontent.com/101941048/212573733-33231fb2-5de1-4d47-bcc9-a7c503856a78.png)

The elbow curve indicates "n_clusters=4" is the best k number. By running the KMeans model, the clusters can be predicted and a new DataFrame was generated by concatentating the crypto_df and pca_df DataFrames, then adding the CoinName back with a Class column. 

## Cryptocurrency Result Visualizations:

### Resulting 3D-Scatter Plot Using PCA data and the Clusters:
![3D_Scatter_PCA Clusters](https://user-images.githubusercontent.com/101941048/212573777-66bea2b9-9075-4655-883b-d23a39f5ea5f.png)

### New Dataframe with Scaled Data Using the clustered_df DataFrame Index:
![plot_df_scaledClusteredData](https://user-images.githubusercontent.com/101941048/212574084-3f89529d-4eed-4637-9560-87b35e87decf.png)

### An Scatter PLot Using the TotalCoinsMined and TotalCoinSupply Data from the Above DataFrame:
![hvplot_scatter_TotalCoinsMine_TotalCoinSupply](https://user-images.githubusercontent.com/101941048/212573783-e5fcb80e-4dcb-44dd-addd-0631d59c0d17.png)

Plotly Express was utilized to visualize the distinct groups that correspond to the 3 PCAs created during the analysis.

## Summary:
As stated prior to beginning the analysis, Accountability Accounting is seeking to is seeking to offer a new cryptocurrency investment portfolio to interested customers. This analysis has reviewed all of the currently traded cryptocurrencies on the market and found that they are best grouped into 4 different classes. This classification system will allow Accountability Accounting to direct its customers to select from the classes based upon the investment goals they have. 

Moving forward, it is important for Accountability Accounting to keep in mind that cryptocurrencies have generally been unstable in the market and should be suggested with a cautionary statement attached[2]. One of the known issues within cryptocurrency markets is the lack of regulation, overtime their may be improved stability should a regulatory body be put into place[3]. This is to say, cryptocurrency currently trends among the higher risk investments, however, many customers are highly interested in partaking in this market and so offering it within portfolios would be a good option for investors who have been educated on the risks and still wish to partake. Before moving further with crypto offerings, it may be worth considering to contract a professional experienced with cryptocurrencies to further direct the portfolio development.

## Data Resources:
- https://archive.ics.uci.edu/ml/datasets/iris
- https://min-api.cryptocompare.com/data/all/coinlist

## Citations:
- [1] https://www.forbes.com/sites/bernardmarr/2017/12/06/a-short-history-of-bitcoin-and-crypto-currency-everyone-should-read/?sh=208698cf3f27
- [2] De Pace, P., & Rao, J. (2023). Comovement and instability in cryptocurrency markets. International Review of Economics & Finance, 83, 173-200.
- [3] https://www.forbes.com/advisor/investing/cryptocurrency/crypto-market-outlook-forecast/
