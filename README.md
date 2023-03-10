# Equity portfolio investment advisor

[Synthesia AI excerpt](https://share.synthesia.io/929ff00e-fa8e-418d-b67d-756b99c2bc1e)

[Streamlit deployment](https://jha-ayush-equity-analyzer-home-w7xb3c.streamlit.app/) - *WIP*

Utilizing financial ratio metrics and state-of-the-art machine learning techniques such as unsupervised and supervised learning, the Analyzer provides users with valuable insights into the stock market, allowing for informed decision making in regards to buying, selling, or holding stocks.

The user interface of the Equity Analyzer is intuitive and user-friendly, making it accessible for individuals of all levels of financial expertise. Its advanced features allow for the identification of profitable investments and the avoidance of costly mistakes.

The business case for the Equity Analyzer is clear, as it empowers investors of all experience levels to make informed decisions regarding their stock portfolio.


## Setup
Create new environment in Terminal
- `conda create -n streamlit python=3.9`
- `conda activate streamlit`
- `pip install requirements.txt` to install all package dependancies


## Run in localhost
- cd into the app folder where `Home.py` sits
- Run `streamlit run Home.py` in Terminal to start up server in `localhost`


## Technologies
Library versions:

- yfinance         : 0.2.3
- requests         : 2.28.1
- numpy            : 1.21.6
- plotly           : 5.11.0
- pandas_datareader: 0.10.0
- sklearn          : 0.0.post1
- seaborn          : 0.12.1
- pandas           : 1.3.5
- matplotlib       : 3.5.3
- cufflinks        : 0.17.3
- logging          : 0.5.1.2
- streamlit        : 1.17.0



## Method
- Install new env as described above
- Install `yfinance`, `streamlit` and other required packages as described above
- Download & explore historical data from Company's `info` key
- Data setup that predict future prices using historical prices
- Test different Machine Learning models to find the optimal model for user's portfolio strategy
- Improve accuracy


## Download data
- Download stock ticker data from `yfinance`
- Review data structure & info
- Map ticker csv to yfinance historical ticker data
- Define start & end dates
- Data cleanup by removing "Dividends" & "Stock splits" columns
- Drop na values
- Use **252 days** for a one year period




## Machine Learning models

### Unsupervised Clustering
After gathering ticker information of the various S&P500 companies and their sector & market cap information, we decided to first get the count of each companies in the various sectors. We identified the top 10 companies from each sector via market cap & daily returns calculations. After that, we moved ahead with grouping these companies into clusters using K-means and Silhouette scoring. Once the tickers were clustered, the data is passed through Monte Carlo simulation to better normalize the data.


### Supervised Classifiers
After Monte Carlo Simulation we genereated a portfolio dataframe for the group of tickers, calucated returns, multiplied returns and volume with monte carlo weights and also calculated short and long moving averages. We concatenated all data in to a single data frame for the portfolio and did resampling to monthly basis. We used Random Forests, KNN and SVR models to find the better model and predictions after defing X and y variables, training, fitting and predicting values. SVR model had better mean error and r2 values compared to other 2 models.

### Algo Trading
In this project, the team decided to use algorithmic trading, also known as algo trading, to execute trades in financial markets. The specific strategy chosen is called DMAC (Dual Moving Average Crossover), which uses two moving averages to identify potential buy and sell opportunities. The strategy is based on the idea that short-term market movements are influenced by short-term trends, while long-term market movements are influenced by long-term trends. The strategy generates a buy signal when the fast moving average crosses above the slow moving average and generates a sell signal when it crosses below.
One of the issues the team faced was in the initial cleaning up of the data. The team used yfinance to download historical data for multiple tickers in portfolios, but due to limitations, they had to create random portfolios. Another issue they faced was with the datetime, which had duplicates, but the team was able to drop the duplicate values with a little research.
To overcome these issues, the team conducted extensive troubleshooting, including testing the code in sections. The next step for the team is to conduct extensive backtesting to evaluate the performance of the strategy. Overall, the team was able to resolve the issues they faced through a combination of Google searching and troubleshooting.

### Time Series Analysis
Facebook Prophet analysis for baseline ticker prediction


## Next Steps

### Technique
- Figure out way(s) to calcuate amount of money a user can generate if trading with any of the models used in the app
- Streamlit cloud deployment
- Add the ability to perform the clustering on a subset of the data: The script currently performs the clustering on all the data. Adding the ability to perform the clustering on a subset of the data, such as the last 30 days
- Add the ability to compare the results of different clustering techniques/parameters: The script currently only shows the results of a single clustering run. Adding the ability to compare the results of different clustering techniques/parameters, such as different number of clusters or different clustering algorithms, would increase the usefulness of the script.
- Include more error handling

### Improve algorithm(s)
- Additional prediction algorthims can be trained
- App can include Neural Networks, Roboadvisors for a better UI interactivity
- Constrain data to a shorter time frame


