# Prediction of PM2.5(Air Pollutant) Level
PM2.5 is an air pollutant responsible for multiple respiratory issues. The pollution levels in the city have increased over time. I have used the Pollution Level Data from Pollution Control Board (PCB) sensors and Cleair network reference grade sensors from Enviome Research in Kolkata for one year.

The data sources initially considered for building the neural network included latitude, longitude, PM2.5 level, temperature, humidity, rainfall and volumes of traffic at that location. Due to loss and damage of some sensors, some data points are missing. The weather dataset has missing data points and when added to the network, gave a very poor performance. Thus, the model has been trained on latitude, longitude, PM2.5 level, and volumes of traffic at that location.

I created a neural network for spatial interpolation using the above-mentioned data points. Since there are two kinds of devices, I used the Pollution Control Board sensors as an input to the model. The interpolation was done on the Cleair device locations. After multiple experiments, the hyperparameters were fixed with Adam optimizer and a learning rate of 0.01 for regularization. Three activation layers with 8, 8 and 4 activation units gave the best performance. The metrics stored during training are root mean square error.

Datapoints of the neural network: 'Datetime', ‘Ballygunge, Kolkata - WBPCB‘,’Belur Math, Howrah – WBPCB’,’Bidhannagar, Kolkata – WBPCB’,’Fort William, Kolkata – WBPCB’,’Ghusuri, Howrah – WBPCB’,’Jadavpur, Kolkata – WBPCB’,’Padmapukur, Howrah – WBPCB’,’Rabindra Bharati University, Kolkata – WBPCB’,’Rabindra Sarobar, Kolkata – WBPCB’,’Victoria, Kolkata – WBPCB’,’US Diplomatic Post: Kolkata’,’latitude’,’longitude,’pm2.5_val’,’traffic_count’.

The location name columns have the pm2.5 levels recorded at that sensor at the same timestamp. The latitude and longitude columns have the location of the Cleair sensors that are being used to train the model. The pm2.5_val column holds the PM2.5 value recorded at the Cleair sensor. The traffic_count holds the value of the number of vehicles passing through the traffic signal at the nearest location to the Cleair sensor.
 
Implementation details:

Python 3.7

Frameworks:

Tensorflow: 2.3.1

Pandas: 1.1.2

Sklearn

Matplotlib: 3.3.2

FBProphet

The results of the spatial interpolation are as follows:
 
 
Metrics from the sklearn library were used to evaluate the model. When tested on the test data, the model gives an R2 score of 0.69.
The results of the time series model using FBProphet are as follows:
Location 1:
 
 
Location 2:
 
 



These results give an insight into the pollution levels of the city. From the plot it can be observed that, 
•	Daily: Pollution level is high during morning and late evenings.
•	Weekly: Pollution is highest during the middle of the week.
•	Yearly: Pollution levels have reduced significantly since Covid outbreak(March 2020).
•	Pollution levels spiked in January.

These results give an insight into the pollution levels of the city. The findings from this project can be used by legislators and policy-makers to take necessary actions to curb the pollution levels.
