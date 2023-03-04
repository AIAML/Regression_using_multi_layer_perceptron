 <h2> Regression With Multi Layer Perceptron and Tensorflow</h2>
 
 <p> In order to estimate a value using Tensowrflow by Python you need to import the following Packages. </p>
 <code>
 from sklearn.datasets import fetch_california_housing
 from sklearn.model_selection import train_test_split
 from sklearn.preprocessing import StandardScaler
 import tensorflow as tf
 from tensorflow import keras
 import pandas as pd
 import matplotlib.pyplot as plt
 </code>
 
 <H3> Dataset </H3>
 
 <p> After that we must include our dataset. In this project we have used California Housing Prices dataset containing these features :  </p>
 
 <ul>
  <li>Longitude</li>
     <li>latitude</li>
     <li>The age of the building</li>
     <li>number of rooms</li>
     <li>Number of bedrooms</li>
     <li>Mitigation of pollution in the area</li>
     <li>The owner of the houses</li>
     <li>Income</li>
     <li>building price</li>
     <li>Close to the ocean</li>
 <ul>
  
<code> housing = fetch_california_housing()
</code>
<p> Then we need to organise our train,validation and test set. Here in the following we have prepared it: </p>

  
<code>
  x_train_full, x_test, y_train_full, y_test = train_test_split(housing.data, housing.target)
  x_train, x_valid, y_train, y_valid = train_test_split(x_train_full, y_train_full)
 </code>
 
 <p> Next We have to build our model. In this sample we have applied Sequential model of neural network.  </p>
 
 <code> 
 <h3> Model </h3>
 
model = keras.models.Sequential()
</code>
<p> The next step is building our layers. The first layer is formed based on our input. Our Input data is an image which has 28*28 dimenstion. As a consequence our code in python would be:  </p>

<code> 
  model.add(keras.layers.Flatten(input_shape=[28, 28]))
</code>
 
 <p> For selecting your model you have to consider this issue that it takes a while to be proficient in selecting your proper model. In this problem we need to classify images so we have two hidden layer which use 'relu' function. Finally for the last layer we have used softmax function with 10 point which indicates our classes.  </p>
 
 <code>
  model = keras.models.Sequential()
  model.add(keras.layers.Flatten(input_shape=[28, 28]))
  model.add(keras.layers.Dense(300, activation="relu"))
  model.add(keras.layers.Dense(100, activation="relu"))
  model.add(keras.layers.Dense(10, activation="softmax"))
 </code>
 
 <p>
 In addtion, before fitting you can view a summery of your model.
 </p>
 <code>
  model.summary()
 </code>
 <h3> Fit and Evaluate </h3>
 <p>
 The last step is compiling and fiting our model. Pure and Simple
 </p>
 <code>
  model.compile(loss="sparse_categorical_crossentropy", optimizer="sgd", metrics=["accuracy"])
   history = model.fit(x_train, y_train, epochs=30, validation_data=(x_valid, y_valid))
 </code>

<p> 
 For showing every epoch result we can use matplotlib which is available in python and at the beginning we have imported it in our project. Here we have our code using data on <i> history varaible </i> for illustrating.
 </p>
 
 <code>
 
 pd.DataFrame(history.history).plot(figsize=(8, 5))
 plt.grid(True)
 plt.gca().set_ylim(0, 1)  # set the vertical range to [0-1]
 plt.show()

 
 </code>
 <img src='https://raw.githubusercontent.com/AIAML/Multi_Layer_perceptron_using_Tensorflow/master/myplot.png' />
 
 
 
 
 
