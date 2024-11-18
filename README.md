# InvestAware - Stock Prediction Platform

InvestAware leverages cutting-edge machine learning and real-time news sentiment analysis to provide accurate stock predictions. Here's an overview of how it works.

---

## ⚙️ **Backend Overview**

### **STOCK_PREDICTOR**  
The core of the stock prediction engine, this system combines machine learning models (RandomForest, XGBRegressor, GradientBoostingRegressor) with technical analysis indicators and sentiment analysis. It preprocesses data through feature scaling and selection, integrates financial indicators (interest rates, oil prices, VIX), and saves the trained model for reuse. The system tracks progress and logs actions, ensuring transparency in predictions.

### **TEST_ACCURACY**  
Evaluates the accuracy of predictions using historical stock data. The system calculates performance metrics like MAE, RMSE, and directional accuracy. It compares predicted returns with actual returns and visualizes prediction errors. It also tracks confidence intervals for each prediction, ensuring a thorough analysis of model performance over time.

### **NEWS_MANAGER**  
Manages real-time stock-related news using the Google News API, employing a rotating proxy system to avoid rate limits and ensure reliability. The sentiment of article titles is analyzed with NLTK's SentimentIntensityAnalyzer. News is fetched continuously and stored for access through a Flask-powered web interface. The system ensures resilience against API failures with exponential backoff retries and detailed logging.

### **PROXY_MANAGER**  
Handles proxy requests and monitors their health over time. The ProxyHealth class tracks success rates and usage limits, while ProxyManager acquires and caches proxies, ensuring optimal performance. A Flask dashboard offers real-time monitoring, displaying proxy metrics like latency and failure rates. Proxies are automatically banned if performance thresholds are not met.

### **UTILITIES**  
Handles the core of stock price predictions by integrating multiple data sources. It fetches market data (sector performance, indices like S&P 500, NASDAQ, etc.) and technical indicators (RSI, MACD, Bollinger Bands) using Yahoo Finance. It then cleans and processes the data, applies machine learning models (XGBRegressor, GradientBoostingRegressor, etc.), and selects the best-performing model based on R-squared score. Predictions are enhanced with confidence intervals and feature importance, all presented with detailed, color-coded output for better user interaction.

---

## 🛠 **Technologies Used**
- **Machine Learning**: XGBRegressor, GradientBoostingRegressor, RandomForest  
- **Data Sources**: Yahoo Finance, Google News API  
- **Technical Analysis**: RSI, MACD, Bollinger Bands, ATR  
- **Sentiment Analysis**: NLTK SentimentIntensityAnalyzer  
- **Backend Framework**: Flask  
- **Proxy Management**: Custom proxy rotation and monitoring system  
- **Data Handling**: RobustScaler, SelectKBest, Feature Engineering  

---

### **Key Features**  
- **High-Confidence Predictions**: Models with over 90% accuracy.  
- **Real-Time News Integration**: Up-to-date sentiment analysis of market-relevant news.  
- **Comprehensive Performance Metrics**: Detailed logs, accuracy tests, and model evaluations.  
- **Custom Proxy System**: Ensures reliable and scalable news fetching.

InvestAware integrates all of these elements into a seamless platform, designed to help users make better-informed stock predictions with confidence.
