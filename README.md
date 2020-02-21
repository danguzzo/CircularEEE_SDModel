# The Circular EEE SD Model
The Circular EEE SD Model was created with the following purpose: to represent nation-wide long-term dynamics of stocks and flows of EEEs when introducing specific scenarios for Circular Economy strategies implementation.

This effort followed the iterative process prescribed by Sterman (2000): (i.) Problem articulation, (ii.) Formulation of Dynamic Hypothesis, (iii.) Formulation of a Simulation Model, (iv.) Testing and (v.) Policy Design and Evaluation. The model was conceptualised following a dynamic Material Flow Analysis approach. It makes use of public available data of inflows and outflows of EEE products in countries to determine the stocks through time.

Among the critical endogenous submodels are:
- A submodel for **technology adoption** following the Bass diffusion model determines the EEE demand from adoption
- A submodel for the **obsolescence of EEE** through a co-flow structure determines EEE average age in combination to the probability of obsolescence using the Weibull lifetime distribution
- A submodel for the **paths of EEE and WEEE** in a given region comprising first use, second use, remanufacturing, recycling, and disposal connected to mechanisms to verify Circular Economy implementation
- A submodel for the **extraction of material** following a supply chain structure

The model was developed using Vensim® DSS for Windows Version 8.0.7 Double Precision x64.

## Data and model structure

The figure below details the structure for data acquisition and model use.

![Data and models structure](https://github.com/danguzzo/cirularEEE_SDmodel/blob/master/images/circularEEE_v.1structure.jpg)

The model is composed of two complementary portions: *circularEE_v.1retrospective* and *circularEEE_v.1prospective*.

The **retrospective model** makes use of a dataset containing country and EEE specific time series. 

Following, the output of the **retrospective model** is used to calibrate the **prospective model**. Model calibration happens for three reasons: (1) enable the simulation to range from 1980 to 2050 with continuous behaviour, (2) adjust the behaviour of the adoption sub-model to the historic flow of EEE into a region, (3) fine-tune the behaviour of stocks and flows of EEE considering an initial structure in place. 

Finally, different scenarios of Circular Economy strategies implementation can be verified.

Both models are available in the /models/ folder in the original version developed (.mdl) and in a Vensim Model Reader compatible format (.vpmx).
A colour scheme identifies specific input and output variables to facilitate undertanding and use:
- ![#c0ffff](https://placehold.it/15/c0ffff/000000?text=+) blue: dataset input
- ![#ff80c0](https://placehold.it/15/ff80c0/000000?text=+) pink: retrospective model output
- ![#c0ffc0](https://placehold.it/15/c0ffc0/000000?text=+) green: prospective submodel output
- ![#c080c0](https://placehold.it/15/c080c0/000000?text=+) purple: input variables to test CE mechanisms

Reports for both models using the [SDM-Doc](https://www.systemdynamics.org/SDM-doc) (Martinez-Moyano, 2012) documentation tool are available on the /models/reports/ folder. 
In this document one can access an overview of model information, all the model views – which constitute the structure of key submodels –, and a detailed description of each variable used in the model. Unit warnings are detailed using the '†' character.

The model has been extensively tested using data for the **Flat Panel Television (UNU 408)** in the **Netherlands (NL)**. The dataset assembled is available in the /datasets/ folder in the data_NL408.xlsx file.

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

Now, in the retrospective model, one should import the dataset created. The file obtained from importing the data into the model is available in the datasets folder: input_NL408.vdfx. 

The 'potential adoption fraction' must be calibrated by using the variables (a) 'normalised ratio EEE price per PPP' and (b) 'R EEE per household'. The pairs of values to be inserted into 'potential adoption fraction' are constituted by [ai, bi]. This relation means that a certain adoption level is obtained considering the price of the good and the purchasing power of that population. When the price lowers and purchasing power is high enough, a certain percentage of the population will access that technology.

You are trying to make 'adoption purchases' mimic the first peak of 'R EEE commissioning'. 
Once the values for 'potential adoption fraction' are obtained, the output dataset from the retrospective model is used to run the prospective  model. The file obtained from the calibration of the retrospective model is available in the datasets folder: prerun_NL408.vdfx. 

After that, one may verify the fit among the curves of 'historic EEE put on market' (dataset input), 'R EEE in use' (retrospective model output), and 'historic disposal of EEE' (dataset input) to the calculated values of 'EEE commissioning', 'Total EEE in use' and 'disposal of EEE as WEEE'. The graphs are already available in the view '5. Calibration and tests'.

One may also the Theil's inequality statistics structure available in the same view to verify the sources of errros among simulated and imported time series: bias (Um), unequal variation (Us), and unequal covariation (Uc).

If the curves are adequately calibrated, one may start model use.

Following the fit curves obtained considering a Baseline scenario, where the infrastructure levels of CE mechanisms for the Netherlands obtained from secondary research are applied.

![Prospective model calibration](https://github.com/danguzzo/cirularEEE_SDmodel/blob/master/images/circularEEE_v.1prospcalibration.jpg)

## Model use

At this point, one can try some combinations of CE mechanisms to verify the flow of resources.

The following variables influence the implementation of Circular Economy mechanisms in the model:
- lifetime ratio
- second use infrastructure level
- repairing infrastructure level
- remanufacturing infrastructure level
- recycling infrastructure level

Towards a Circular Economy, organisations and governments aim to decrease the inflow of materials and products in the system while keeping them in high use. 
Thus, we recommend you to check how the changes in CE mechanisms influence the stocks and flows of EEE and WEEE in the system.

## Model testing activities

The table below outlines the testing activities performed in the model. Learning outcomes and model changes are described for each activity. Transparency in testing activities and learning outcomes help determine the suitability of the model for the defined purpose.

Test type|Test description|Learning outcomes and model changes
---------|---------------------|-----------------------------------
Boundary adequacy	| Model boundary chart development | Model boundaries defined. Relevant structures have been endogenized. Reliable data for most of the exogenous structures can be obtained from structured databases.
Boundary adequacy	| Model expansion to include the Adoption submodel | Stabilises the transition from retrospective to prospective simulation. Enables verification of resource usage in the face of adoption of a technology.
Structure assessment | Subsystem diagram development | Represents the main concepts and feedback structures used to address the model purpose.
Structure assessment | Model conceptualisation following dynamic Material Flow Analysis concept	| Such an approach relies on the conservation of matter principle. Non-recycled WEEE stock is the sink of the system.
Structure assessment | Application of the mass-balance check (Dangerfield, 2014; Schwaninger & Groesser, 2016) for products and materials |	Permits verification that the model does not gain or lose mass of materials and products.
Structure assessment | Development and testing relevant sub-model parts in isolation to build confidence before aggregate analysis | Every EEE and WEEE flow has been developed and tested isolated from changes in other parts until a plausible behaviour was obtained. 
Structure assessment | Verification of stocks in varied conditions to identify negative values | Leadst to changing model structure or equations. For instance, the 'Available used-EEE' stock had to be constrained. The following assumption was implemented: these products will rather move into second use, then remanufacturing, then recycling. In that order of preference.
Dimensional adequacy | Use of parameters with real-world meaning when modelling | Every parameter receives a name and description that clearly identifies its meaning. One clear ad hoc variable is 'effect of PPP on the average number of EEE per household', that helps to calculate EEE demand from recurrent purchases of adopters based on historical data.
Parameter assessment | Elaboration of a step-by-step guide to calibrating relevant partial models | Enables to calibrate the behaviour of EEE adoption from retrospective data available from 1980-2015.
Extreme conditions | Bounding the use of the model by levels of CE mechanisms implementation | The 0 to 4 infrastructure level indexes bound the model. It decreases the potential of unexpected behaviour due to extreme conditions. In the other hand, it may decrease the possibilities for insights.
Extreme conditions | Bounding auxiliaries and flows with potential extreme behaviour | For instance, a combination of MIN and one-minus function was used to prevent the 'fraction of decommissioned EEE introduced to E-waste market' to be negative.
Extreme conditions | Shocks and extreme condition testing	| For instance, tested the inflow of a shipment of used products as 'Available used-EEE' with a given average age in the middle of the adoption process, mimicking what happens in countries under development. Mass balance is maintained, EEE and WEEE flows provide insights.
Integration error	| Testing the model using RG4 of 1 year to 0.125-year time steps | Results are not sensitive to these choices in the time step. Nevertheless, the supply chain delays are proportional to the time step.
Behaviour Reproduction | Setting up a dashboard to fit the prospective model to external data and data calculated in the prospective model | Helps to calibrate the model through behaviour reproduction of the following variables: 'EEE commissioning' and 'historic annual EEE put on market'; ‘Total EEE in use' and 'R EEE in use'; ‘disposal of EEE as WEEE’ and ‘historic disposal of EEE’
Behaviour Reproduction | Application of descriptive statistics tools to calibrate the model – Theil inequality statistics (Oliva, 1995; Sterman, 2000) |	A structure to verify bias, unequal variation, and unequal covariation of simulated and input variables can be used to verify the fit among variables above. Holds potential to automate steps of the calibration process.
Family member test | Using Netherlands (NL) and Estonia (EST) data for Fridges (UNU 108) | NL and EST provide good sources for data. EST data is harder to obtain when closer to 1980 - former USSR state. The prospective model can be calibrated using the retrospective data available for both cases. Apart from the fact that NL and EST are from different stratum in vanStraalen2016 analysis, they are both mature markets for fridges. This way, comparing the representation of EEE dynamics under CE strategies for both regions does not bring many different insights.
Family member test | Using (Netherlands) NL data for Fridges (UNU 108) and Flat Display Panel TVs (UNU408) | The prospective model can be calibrated using the retrospective data available for both cases (108NL and 408NL). It enables the discussion of the general implementation of CE mechanisms in EEE. As the adoption curve for Flat Display Panel TVs is similar to the adoption of a technology that becomes mainstream, it is more useful to visualise CE strategies implementation.

## Model limitations

The table below contains the model limitations and learning outcomes from potential tests. These tests are out of scope for this modelling effort, but they indicate future endeavours to enhance cofidence to the model, or reframe the model purpose. Model limitations present an opportunity for other researchers and decision-makers to enhance the Circular EEE SD Model.

Limitation|Potential learning outcomes
----------|---------------------------
Limited explanatory ability of the adoption mechanism |	Further understanding the types of adoption patterns and their influence in the effects of CE strategies implementation. 
Limited explanatory ability of the types of purchasing | Further understand how first purchases, recurrent purchases to replace, and additional purchases influence and are influenced by CE strategies implementation. 
Limited explanatory ability of the types of obsolescence | Increase understanding of the influence of psychological and functional dimensions of obsolesce.
Limited implementation of non-transaction based CE strategies | Increase understanding of the impacts of sharing and servitization strategies
Limited explanatory ability of CE mechanisms leverages |	Increase understanding of the incentives for CE mechanisms implementation. 

## References

de Almeida, A., & Rosenfeld, A. H. (1987). Demand-Side Management and Electricity End-Use Efficiency (Vol. 149; A. T. Almeida & A. H. Rosenfeld, Eds.). https://doi.org/10.1620/tjem.162.269

Dangerfield, B. (2014). Systems thinking and system dynamics: A primer. Discrete-Event Simulation and System Dynamics for Management Decision Making, 9781118349(2007), 26–51. https://doi.org/10.1002/9781118762745.ch03

Forti, V., Baldé, C. P., & Kuehr, R. (2018). E-Waste Statistics.

International Monetary Fund. (2019). World Economic Outlook. Retrieved from https://www.imf.org/external/datamapper/datasets/WEO

Martinez-Moyano, I. J. (2012). Documentation for model transparency. System Dynamics Review, 28(2), 199–208. https://doi.org/10.1002/sdr.1471

Morrison, G. (2017). Are TVs really cheaper than ever? We go back a few decades to see. Retrieved from https://www.cnet.com/news/are-tvs-really-cheaper-than-ever-we-go-back-a-few-decades-to-see/

Oliva, R. (1995). A Vensim® Module to Calculate Summary Statistics for Historical Fit. Dynamica, 10, 51–56.

PricewaterhouseCoopers. (2017). The World in 2050. Retrieved from https://www.pwc.com/gx/en/issues/economy/the-world-in-2050.html

Schwaninger, M., & Groesser, S. (2016). System Dynamics Modeling: Validation for Quality Assurance. Encyclopedia of Complexity and Systems Science, 1–20. https://doi.org/10.1007/978-3-642-27737-5

Statistics Netherlands. (n.d.). CBS Open data StatLine. Retrieved from https://opendata.cbs.nl/statline/portal.html?_la=en&_catalog=CBS

Sterman, J. D. (2000). Business dynamics: Systems thinking and modeling for a complex world. In Management. https://doi.org/10.1057/palgrave.jors.2601336

van Straalen, V. M., Roskam, A. J., & Baldé, C. P. (2016). Waste over Time. Retrieved from https://github.com/Statistics-Netherlands/ewaste

Zeng, X., & Li, J. (2016). Measuring the recyclability of e-waste: An innovative method and its implications. Journal of Cleaner Production, 131, 156–162. https://doi.org/10.1016/j.jclepro.2016.05.055
