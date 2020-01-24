# cirularEEE_SDmodel
The Circular EEE SD model was created with the following purpose: to represent region-wide long-term dynamics of stocks and flows of EEEs when introducing specific scenarios for Circular Economy strategies implementation.

The model was developed using Vensim® DSS for Windows Version 8.0.7 Double Precision x64.

The data and models structure utilised are detailed below:
![Data and models structure](https://github.com/danguzzo/cirularEEE_SDmodel/blob/master/images/circularEEE_v.1structure.jpg)

The model is composed of two complementary portions: circularEE_v.1retrospective and circularEEE_v.1prospective. 
The retrospective model makes use of a datased containing country and EEE specific time series. Following, the output of the retrospective model is used to calibrate the prospective model. Finally, different scenarios of Circular Economy strategies implementation can be verified.

Both models are available in the /models/ folder on the original version developd (.mdl) and on a Vensim Model Reader compatible format (.vpmx).
Reports for both models using the [SDM-Doc](https://www.systemdynamics.org/SDM-doc) documentation tool are available on the /models/docreports/ folder.

The model has been extensively tested using data for the Flat Panel Television (UNU 408) in the Netherlands (NL). The dataset assembled is available in the /datasets/ folder in the data_NL408.xlsx file.
