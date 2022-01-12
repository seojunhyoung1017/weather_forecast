# Managing ML data and models for weather forecast

    Description
- Why weather forecasting?
    1. In general, domain experts define climate as a ‘complex system’. While there are a lot of interpretations about it, we can consider ‘complex’ to be ‘unsolvable in analytical ways’. Therefore, it is true that machine learning is not yet used in weather forecasting.

    2. However, if we can solve this problem and be able to establish machine learning models to predict the weather, there will be a huge benefit from it. Currently, numerous satellites and observation equipment are used for weather forecasting, and if accurate weather forecasting is possible through machine learning modeling, a lot of cost reduction and convenience can be obtained.

    3. While this is highly challenging, this project is aimed to find out if there is any single possibility of applicability of machine learning in the weather forecast.

- How to extract and store the historical weather data?
    1. This project will use the world weather online API to extract historical data, which provides historical data of temperature, weather description, wind speed, etc. from July 2008 to a recent date. 

    2. The system will query the API to call the historical data from July 2008 to a recent date, and the system will extract features in raw data and save them in the system’s data frame. Maximum, minimum, and average temperatures will be extracted from raw data and stored in the data frame. 

    3. Since it is highly time-consuming to query API multiple times to use a system, the system will upload the extracted features of data into the Firebase cloud database. In Firebase, features will be classified by city name and stored in each city category.

    4. As users operate the system, more historical weather data of different cities will be stored in Firebase, and the system can simply load the data from Firebase for analysis without calling API. Figure A is showing the screenshot of the Firebase database as bellows:

<p align="center">
  <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture1.png">
</p>
<p align="center">
    (Figure A)
</p>

- Which machine learning model will be applied?
    1. ARIMA model is a powerful algorithm especially when you aim to predict future values based on past values in time-series data. Since this project is handling time-series data, the ARIMA model will be applied for the prediction of future temperature.

    2. ARIMA model includes parameters p, d, and q, and each parameter represents the number of lag observations in the model, the number of times that the raw observations are differenced, and the size of the moving average window.

    3. Therefore, depending on parameters, there are many kinds of ARIMA models, so, the system will evaluate each model to find a best-fitting model for the data set. Auto-Arima function will be used for this process, this function will calculate Akaike’s Information Criterion (AIC) for every possible ARIMA model, and the one that has the lowest AIC will be selected for the model to predict the weather.

    4. Figure B shows the example running of the Auto-ARIMA function in the system using a sample dataset of Los Angeles. In this case, ARIMA (2,1,1) is the best fitting model for the sample dataset, and this model will be used for future prediction.

<p align="center">
  <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture2.png">
</p>
<p align="center">
    (Figure B)
</p>

- What does the system provide for the users and how users can operate your system?
    1. This project uses Jupyter Notebook as a user interface, so, to operate the system users just need to click the cells consecutively. Users need to input the city name to the system to query the API the first time, if the data of that city is already stored in a cloud database, the system will not call the API, instead, the system will load the data from the Firebase. Then, the system will visualize data, metadata, extracted features, and prediction results for the users. Moreover, the system will plot the line chart of the historical temperature, and a comparison between the test set and prediction from the training set will be also plotted as a line chart.

    2. Examples of visualized data that can be obtained by users are as follows, the examples are presuming that users input the city name as Los Angeles.

    3. Figure C is showing the raw data that users can obtain.
    
    <p align="center">
    <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture3.png">
    </p>
    <p align="center">
    (Figure C)
    </p>

    4. Figure D is showing the extracted features of the data that users can obtain.


    <p align="center">
    <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture4.png">
    </p>
    <p align="center">
    (Figure D)
    </p>

