# NPS-Correlation
Architecture of NPS Correlation: 
1.Sequence Problems (Many-to-One) with a Single Feature: Here I have the LSTM model for time series data forecasting and we have Data of a company with the stock prices of past 'X' days opening, closing,high and low. So initially, the data has to be perfect, for that extract only the closing stock price coloumn has to be calculated and stored in an array. 
Now, we have to split the data into train and test sets. So let us assume there are 'Y' days of closing stock price data. Now create data in 'N' time steps and convert into an array.Then as the input should be in 3D shape ,we should reshape our data into [samples, time-steps, features] having 1600 days of data which means 'Y' samples and usually the time steps are taken in the range of 50-80. The feature which is the only one used and taken into consideration is the 'closing time'. Now this will create a 3D form to our input which is accepted by the LSTM. 
How to build the LSTM? :
After cleaning the data and making it ready, build a LSTM model, first importing modules from 'keras' library like 'sequential' (for initializing the network), 'dense'(adding densely connected network layer), 'lstm' and 'dropout'(this adds dropout layer which prevents over fitting)
Initializing Lstm layer with: no. of neurons ,return sequence and input shape
After initializing connect a dropout layer with specifiyng small percentage to dropout(I found out this layer can be skipped as it can reduce the performance of the model) 
Then connect hidden dense layer with activation function 'Adam' which will work for our model and also with the no. of neurons in this layer as explained earlier in the initialization
Final layer dense layer (output layer) is made with same 'Adam' activation function and here the No. of neuron we use is '1' as we need only one output (next day stock price).
Now, for compilation use 'ADAM' optimizer, here the loss is 'mean sq error' ,adam optimizer works on each parameter to give more accurate mean sq error which is enough for our model.
Fit the model with input data created and let the no. of epochs and batch size,
Making prediction test data:
By making same changes as made in train data ,creating same no. of time steps and converting the data in 3D shape etc.
Predicting the stock price!: 
predict the stock price from the test data
Check :
comparing the actual price to the predicted price would suggest the capability off  this LSTM  architecture
ProTip! Use n and p to navigate between commits in a pull request.

 
