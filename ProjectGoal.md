# Banking-Fraud
The Anti "Catch Me If You Can". To identify fraudlant banking activity as it happens and minimize the effect of identity theft on individuals. 

# Datasets
- Paysim synthetic dataset of mobile money transactions. Each step represents an hour of simulation. This dataset is scaled down 1/4 of the original dataset which is presented in the paper "PaySim: A financial mobile money simulator for fraud detection". Includes: 
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

# Modeling Strategy
- Break up events into types of transactions. These are as follows. Each new record will be cross-referenced against a multi-class classification model that predicts each nameOrig for it's likelihood of having fraudulant activity.
  
# End Goal

