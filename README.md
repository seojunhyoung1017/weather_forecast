# Managing ML data and models for weather forecast

    Description
a.	Why weather forecasting?\
i)	Since my undergraduate major is Civil Engineering, during my undergraduate study, I have a lot of experience to handle weather data. Also, I used to work on a lot of projects in handling precipitation data and temperature data; therefore, I selected to apply machine learning in weather forecasting

ii)	In general, domain experts define climate as a ‘complex system’. While there are a lot of interpretations about it, we can consider ‘complex’ to be ‘unsolvable in analytical ways’. Therefore, it is true that machine learning is not yet used in weather forecasting.

iii)	However, if we can solve this problem and be able to establish machine learning models to predict the weather, there will be a huge benefit from it. Currently, numerous satellites and observation equipment are used for weather forecasting, and if accurate weather forecasting is possible through machine learning modeling, a lot of cost reduction and convenience can be obtained.

iv)	While this is highly challenging, this project is aimed to find out if there is any single possibility of applicability of machine learning in the weather forecast.

b.	How to extract and store the historical weather data?\
i)	This project will use the world weather online API to extract historical data, which provides historical data of temperature, weather description, wind speed, etc. from July 2008 to a recent date. 

ii)	The system will query the API to call the historical data from July 2008 to a recent date, and the system will extract features in raw data and save them in the system’s data frame. Maximum, minimum, and average temperatures will be extracted from raw data and stored in the data frame. 

iii)	 Since it is highly time-consuming to query API multiple times to use a system, the system will upload the extracted features of data into the Firebase cloud database. In Firebase, features will be classified by city name and stored in each city category.

iv)	As users operate the system, more historical weather data of different cities will be stored in Firebase, and the system can simply load the data from Firebase for analysis without calling API. Figure A is showing the screenshot of the Firebase database as bellows:
![image](https://user-images.githubusercontent.com/70517651/149046559-457da988-92c3-4e45-85d7-1d1d257591d8.png)
