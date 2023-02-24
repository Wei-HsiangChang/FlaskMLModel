# FlaskMLModel
## Set up environment:

1. Get Python, pip, VENV installed

2. Activate virtual environment:<br> 
   ```source .env/bin/activate``` 

3. Add libraries from requirements file into virtual environment:<br> 
   ```pip install -r requirements.txt```


## Build App:

### Build ML Model:

Use Google Colab to build ML model and saved as .ipynb file.

Process:

1. !wget to get pickle file into directory

2. Use pandas to read pickle file from directory:<br> 
   pd.read_pickle()

3. Use plotly.express:<br> 
   px.scatter(x=ages, y=heights, title="Height vs Age Of People", labels={'x': 'Age(years)', 'y': ‘Height(inches)'}) or data.plot.scatter(x='Age', y=‘Height') to get scatter plot of data

4. Turn data into numpy array to fit into a linear regression model:<br> 
   ages.to_numpy()
     
   - Reshape as 1 feature:<br> 
   ages_np.reshape(len(ages), 1) 

5. Create scikit-learn linear model:<br>  

   model = LinearRegression().fit(ages_np_reshaped, heights_np)
 
   - Make prediction:<br> 
	 x_new = np.array(list(range(19))).reshape(19, 1)<br> 
   preds = model.predict(x_new)
  
   - Add tracing line:<br> 
   fig.add_trace(go.Scatter(x=x_new.reshape(19), y=preds, mode='lines', name='Model'))

6. Dump to file<br> 
   Use joblib to dump and load model
  
7. Create a method to accept input array, training data, and output file name to make the ML model picture output to the file.  

### Build Flask UI
Import Flask and run app in command: flask run

1. Make UI to let user input the value, and get ML model result
   - render href as variable in different content:<br>
   render_template('index.html', href=‘static/base.svg’), ```<img src="{{ href }}" height=600 />```

2. Import uuid to produce random file name when requesting
