# cirularEEE_SDmodel
The Circular EEE SD model was created with the following purpose: to represent region-wide long-term dynamics of stocks and flows of EEEs when introducing specific scenarios for Circular Economy strategies implementation.

The model was developed using Vensim® DSS for Windows Version 8.0.7 Double Precision x64.

## Data and model structure

The figure below details the structure for data acquisition and model use.

![Data and models structure](https://github.com/danguzzo/cirularEEE_SDmodel/blob/master/images/circularEEE_v.1structure.jpg)

The model is composed of two complementary portions: *circularEE_v.1retrospective* and *circularEEE_v.1prospective*.

The **retrospective model** makes use of a dataset containing country and EEE specific time series. 

Following, the output of the **retrospective model** is used to calibrate the **prospective model**. 

Finally, different scenarios of Circular Economy strategies implementation can be verified.

Both models are available in the /models/ folder in the original version developed (.mdl) and in a Vensim Model Reader compatible format (.vpmx).
A colour scheme identifies specific input and output variables to facilitate undertanding and use:
- ![#c0ffff](https://placehold.it/15/c0ffff/000000?text=+) blue: dataset input
- ![#ff80c0](https://placehold.it/15/ff80c0/000000?text=+) pink: retrospective model output
- ![#c0ffc0](https://placehold.it/15/c0ffc0/000000?text=+) green: prospective submodel output
- ![#c080c0](https://placehold.it/15/c080c0/000000?text=+) purple: input variables to test CE mechanisms

Reports for both models using the [SDM-Doc](https://www.systemdynamics.org/SDM-doc) documentation tool are available on the /models/docreports/ folder. 
In this document one can access an overview of model information, all the model views – which constitute the structure of key submodels –, and a detailed description of each variable used in the model. Unit warnings are detailed using the '†' character.

The model has been extensively tested using data for the Flat Panel Television (UNU 408) in the Netherlands (NL). The dataset assembled is available in the /datasets/ folder in the data_NL408.xlsx file.

## Data gathering

First, one may choose a specific country and EEE.

He/she may obtain the values for the variables mentioned on the 'Data preparation' table for the specified range. 
Sources are mentioned for the specific case of Flat Panel Television in the Netherlands. For other countries and EEE types, further research may be needed.

Class|Variable|Range|Source
-----|--------|-----|------
|Country-specific|purchasing power parity per capta|1980-2050|International Monetary Fund (2019); PricewaterhouseCoopers (2017)
|Country-specific|total households|1980-2050|Statistics Netherlands (n.d.)
|Country-specific|population|1980-2050|Statistics Netherlands (n.d.)
|EEE-specific|EEE average unit weight|1980-2020|van Straalen et al (2016)
|EEE-specific|EEE unit price|1980-2020|Morrison (Morrison, 2017)
|EEE-specific|Weibull scale|constant|Forti et al. (2018)
|EEE-specific|Weibull shape|constant|Forti et al. (2018)
|EEE-specific|recyclability|constant|Zeng and Li (2016)
|Country_EEE-specific|historic EEE put on market|1980-2020|van Straalen et al (2016)
|Country_EEE-specific|historic disposal of EEE|1980-2020|van Straalen et al (2016)
|Country_EEE-specific|initial adoption fraction|1980|de Almeida and Rosenfeld (1987, p. 80)

## Model calibration

Now, in the retrospective model, one should import the dataset created. 

The 'potential adoption fraction' must be calibrated by using the variables (a) 'normalised ratio EEE price per PPP' and (b) 'R EEE per household'. The pairs of values to be inserted into 'potential adoption fraction' are constituted by [ai, bi]. 

You are trying to make 'adoption purchases' mimic the first peak of 'R EEE commissioning'. 
Once the values for 'potential adoption fraction' are obtained, the output dataset from the retrospective model is used to run the prospective  model.

After that, one may verify the fit among the curves of 'historic EEE put on market' (dataset input), 'R EEE in use' (retrospective model output), and 'historic disposal of EEE' (dataset input) to the calculated values of 'EEE commissioning', 'Total EEE in use' and 'disposal of EEE as WEEE'. The graphs are already available in the view '5. Calibration and tests'.

One may also the Theil's inequality statistics structure available in the same view to verify the sources of errros among simulated and imported time series: bias (Um), unequal variation (Us), and unequal covariation (Uc).

If the curves are adequately calibrated, one may start model use.

## Model use

At this point, one can try some combinations of CE mechanisms to verify the flow of resources.

The following variables may influence the implementation of Circular Economy mechanisms in the model:
- lifetime ratio
- second use infrastructure level
- repairing infrastructure level
- remanufacturing infrastructure level
- recycling infrastructure level

In a Circular Economy, organisations and institutions aim to decrease the inflow of materials and products in the system while keeping them in high use. 
Thus, we recommend you to check how the changes in CE mechanisms influence the stocks and flows of EEE and WEEE in the system. 

## References

de Almeida, A., & Rosenfeld, A. H. (1987). Demand-Side Management and Electricity End-Use Efficiency (Vol. 149; A. T. Almeida & A. H. Rosenfeld, Eds.). https://doi.org/10.1620/tjem.162.269

Forti, V., Baldé, C. P., & Kuehr, R. (2018). E-Waste Statistics.

International Monetary Fund. (2019). World Economic Outlook. Retrieved from https://www.imf.org/external/datamapper/datasets/WEO

Morrison, G. (2017). Are TVs really cheaper than ever? We go back a few decades to see. Retrieved from https://www.cnet.com/news/are-tvs-really-cheaper-than-ever-we-go-back-a-few-decades-to-see/

PricewaterhouseCoopers. (2017). The World in 2050. Retrieved from https://www.pwc.com/gx/en/issues/economy/the-world-in-2050.html

Statistics Netherlands. (n.d.). CBS Open data StatLine. Retrieved from https://opendata.cbs.nl/statline/portal.html?_la=en&_catalog=CBS

van Straalen, V. M., Roskam, A. J., & Baldé, C. P. (2016). Waste over Time. Retrieved from https://github.com/Statistics-Netherlands/ewast

Zeng, X., & Li, J. (2016). Measuring the recyclability of e-waste: An innovative method and its implications. Journal of Cleaner Production, 131, 156–162. https://doi.org/10.1016/j.jclepro.2016.05.055
