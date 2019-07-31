# Banking-Fraud
The Anti "Catch Me If You Can". To identify fraudlant banking activity as it happens and minimize the effect of identity theft on individuals. 

# Datasets
- Chicago Crime Data Sets: 
https://www.kaggle.com/ntnu-testimon/paysim1    
Includes:    
    <strong>step</strong>
    <em>Maps a unit of time in the real world. In this case 1 step is 1 hour of time.</em>
    
    <strong>type</strong>
    <em>CASH-IN, CASH-OUT, DEBIT, PAYMENT and TRANSFER</em>
    
    <strong>amount</strong>
    <em>amount of the transaction in local currency</em>
    
    <strong>nameOrig</strong>
    <em>customer who started the transaction</em>
    
    <strong>oldbalanceOrg</strong>
    <em>initial balance before the transaction</em>
    
    <strong>newbalanceOrig</strong>
    <em>customer's balance after the transaction.</em>
    
    <strong>nameDest</strong>
    <em>recipient ID of the transaction.</em>
    
    <strong>oldbalanceDest</strong>
    <em>initial recipient balance before the transaction.</em>
    
    <strong>newbalanceDest</strong>
    <em>recipient's balance after the transaction.</em>
    
    <strong>isFraud</strong>
    <em>identifies a fraudulent transaction (1) and non fraudulent (0)</em>
    
    <strong>isFlaggedFraud</strong>
    <em>flags illegal attempts to transfer more than 200.000 in a single transaction.</em>

- Weather in Chicago: NOAA will provide data from stations in Chicago on a daily basis for free.
https://www.ncdc.noaa.gov/cdo-web/. This includes primarily temperature maxs and mins. Most of the other fields are missing.

- Headlines? Social tension indicators?
- Gun availability indicators? 
- Gang rivalry indicators? 
- Housing price indicators; social status change data


# Modeling Strategy
- Break up events into types of crime. These are as follows. Each new day will be cross-referenced against a multi-class classification model that predicts each block for it's likelihood of having any of 7 types of criminal activity.
    - Kidnapping
    - Sexual assault 
    - Homocide
    - Motor vehicle theft 
    - Weapons violation
    - Battery
    - Theft
- Link with weather data
- Build a multi-class classifier to predict each type of crime
- Use sequential methods to model the add-on effect; because of what happened earlier in the year, this will happen. Most likely will need to model the sequence in a discrete window of time: One month? One quarter? One year? Will need to experiment here to find the right windo. 

Potentially use multi-class classification to rank blocks in the city based on their likelihood of having a type of crime in the coming day, given the weather forecast and all previously known criminal activity. 


Potentially use LSTM's to capture both the level of complexity and the sequential element. 

Open question: how do we standardize the sequence of both criminal events per block and weather events per block that lead up to the criminal event? Monthly? Yearly? For 2018 maybe just include the sequence of the last month. This means we need to chunk the data into month sequences that go into the LSTM's.

Is it actually better to think about this problem as forecasting? Where we're forecasting the level of crime? Unknown.

# End Goal
Heatmap that predicts crime multiple days in advance. Final system should be a website that queries the Chicago data portal and local weather sensors every day, retrains the model over night, and generates new predictions for the day's criminal activity.

Rather than getting side-tracked about the research goals, it might be more valuable to build the website first, and then load in new models over time as we ship them.
