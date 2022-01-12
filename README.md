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

    5. Figure E is showing the metadata of the data that users can obtain.
    
    <p align="center">
    <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture5.png">
    </p>
    <p align="center">
    (Figure E)
    </p>
    
    6. Figure F is showing the line chart of temperature that users can obtain.
    
     <p align="center">
    <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture6.png">
    </p>
    <p align="center">
    (Figure F)
    </p>
    
    7. Figure G is showing the line chart of comparison between the test set and prediction using the training set. This example shows the model is not fitting well with the data; however, users can add seasonality parameters in their model to get a well-fitting result; however, my local machine was not able to handle the high-performance computing so that I am noticing that this example is not the best example. If users use a high-computing power machine, they can get the best model for their data.
    
    <p align="center">
    <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture7.png">
    </p>
    <p align="center">
    (Figure G)
    </p>
    
    8. Figure H is showing the prediction result that can be obtained by users.
    <p align="center">
    <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture8.png">
    </p>
    <p align="center">
    (Figure H)
    </p>
    
    System architecture, components
- Figure I is showing the system architecture and components as a diagram bellows:
    <p align="center">
    <img src="https://github.com/seojunhyoung1017/weather_forecast/blob/main/images/Picture9.png">
    </p>
    <p align="center">
    (Figure I)
    </p>

- The users can explore the user interface which is connected to API, cloud database, and machine learning models. And user interface can query the API and get an output, train the model and get a prediction output, and store or load the data from cloud database as explained above.

    Learning experiences
- Since this project was my first project to handle machine learning models and the data. It was challenging for me to establish the machine learning model and get a prediction output. But, after finishing this project, now I think I can handle more advanced machine learning projects based on real-life problems because I learned a system flow of the machine learning analysis.

- The project aimed to provide an intuitive interface for users who have no computer science background. Therefore, I should consider more about users and think about how I can provide the best user interface for users’ convenience. So, the user interface was configured to visualize all the results by the users only entering the city name. In the real world, most users do not know about the computer language, so this was very reasonable, and I got a lesson on how to think from the user’s perspective.

- Through the project, I gained a lot of skills to carry out the data science project by myself. Firstly, I have learned how to establish a database efficiently to analyze the data. Secondly, I have learned how to build machine learning models for the data and perform the prediction. Lastly, I have learned how to make a pragmatic code to manage the data. After many trials and errors, I came to think about how to gain the results in the shortest time, finally, I gained knowledge about how to construct the optimal code and establish the system architectures.
