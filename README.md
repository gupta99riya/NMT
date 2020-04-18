# Neural Machine Translation 
Neural Machine Translation use to predict machine readable date  from human readable date.

**Objective:** There are variety of possible human readable formats (e.g. "the 29th of August 1958", "03/30/1968", "24 JUNE 1987"), this network will convert that into standardized, machine readable dates (e.g. "1958-08-29", "1968-03-30", "1987-06-24"). 

**Approach:** Here data will be processed by getting indexes corresponding to each of the input date using dictionaries created in previous step. Also, the length of each row in the process data will be of same size using padding. Later, one hot encoding is created for the indexes data.

- **Data Extraction:** Data used for this analysis is from [Faker](https://pypi.org/project/Faker/), a Python package that generates fake data for you. It can generate address, name, text, date etc..

  Following are the steps used for data preparation:
  - Fetching data from Faker and creating human readable and machine readable dates.
  - Creating a list of both the dates and dictionary of human vocab and machine vocab by assigning index to each of the unique character/integer.

    
- **Algorithm Used:** Sequence to Sequence Model using Attention Mechanism

    Sequence to Sequence model uses an *Bidirectional LSTM* arcitecture so that the model will have forward and backward information (in the form of activations) at every step so that the model will learn from previous as well later instances. Attention mechanism is used by the network to identify how much focus to be made for one partcular time step as information from multiple time step will be folating into the prediction for that instance.

    A small neural network is used to identify the attention weights using the activation and LSTM layer of the decoder vector. Context is calculated using the attention weights and activated factors which will be passed as the information to the Post-attention LSTM layer of decoder.

    First getting activation from Bidirectional LSTM, then one_step_attention is performed Ty times to calculate context. Following that another layer of LSTM will predict y.
 

**Next Step:**
 - Model can be trained on higher size of data with higher number of epochs given a better infrastructure
 - Currently the model is trained full dataset but can be trained on a sample and tested on another sample to understand the overfitting.
 - Different parameters can be tried like learning rate, units etc.
 - Different optimization function can be tried like LeakyRelu etc. 
 - We can play more around the architechure adding more layers. 

**How to test the model**
 - To test the model- sample needs to be provided to the model 
