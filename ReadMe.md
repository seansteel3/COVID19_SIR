
# COVID19_SIR

<!-- Introduction -->
## Introduction
The COVID19_SIR project is a mathematical modeling project for the spread of COVID-19.  This project aims to explore disease dynamics through a basic epidemiological compartmental model known as the Survival Infectious
Recovered Deceased model, or SIRD for short. 

This model builds off the basic SIR (Susceptible Infectious Recovered/Removed) model by specifying a compartment for deceased individuals as opposed to simply lumping removed and recovered together. Due to the fact COVID-19 is a rapidly evolving public health crisis, the data surrounding current infections may not be accurate, and the error in reporting infections is likely to be highly heteroskedastic. However, death data, while still prone to error, is less likely to be critically compromised like infection data. Under this context SIRD model is considered a more simple model than the basic SIR model, since death data to fit directly to estimate the parameters.


In addition to the obvious intrigue of exploring the nature of pandemics, this project is also intended as a personal learning project since it will serve as the first exposure to differential equation modeling. 

<!-- The Model -->
## The Model

The SIRD model is made up of four compartments, one for each possible state of the populaton. These four compartments (susceptible, infectious, recovered, deceased) are governed by a system of differential equations:

Susceptibles change at a rate equal to:

![equation](https://bit.ly/2RMKyvV)

Infectious change at a rate equal to:

![equation](https://bit.ly/3w39Q7S)

Recovered change at a rate equal to:

![equation](https://bit.ly/3uJoXD6)

Deseased change at a rate equal to:

![equation](https://bit.ly/3ocQiLh)

Where beta is the force of infection, N is the total population, lambda is the probability of death, rho is the rate of recovery, and eta the rate of death. For simplicity, this model will begin with lambda set to 0.015, or equal to the estimated overall probability of death from COVID-19 according to the CDC.

The basic reproductive number, Ro, can also be derived from the SIRD equations. Ro is equal to the force of infection, beta, divided by the rate of removal, gamma. 

![equation](https://bit.ly/3fkltk6)

![equation](https://bit.ly/3obTDKy)

## Project Current State and Future Directions

Currently the project contains a data cleaning RMD file, which munges the raw data obtained from the Johns Hopkins COVID-19 dashboard. Additionally, data for 8 US states is presently uploaded, as well as miscellaneous data for Italy and a dirty whole US data set.

Further, a single file formulating an initial SIRD model for the state of New York is currently present. This file explores the intricacies of differential equation modeling and estimating the basic reproductive number by a number of methods. At the moment, all current models fail to converge to a realistic result, regardless of the statistical packages used or underlying assumption of the statistical distribution of the data.

This failure likely stems from a data cleaning or even a raw data problem since the log-likelihood profiles for all of the models tended to be devoid of any clear optima, and/or contained undefined optima when parameters were bounded to realistic solutions (ie: Ro between 1-7). An incorrectly specified model or a poorly constructed objective function cannot be ruled out as an alternative cause for the convergence failure, but these issues seem to be the less likely culprit. Mainly because a similar basic SIR model with L2 norm and MLE objective functions were tested on measles outbreak data in Niamey Niger yielding high quality results. The only substantive difference between this project’s modeling and the Niamey Niger outbreak model is the fact that this model fits its parameters to death data rather than to infection data. Therefore, if the issue does not stem from incorrect data processing, the next most likely cause is in the method for fitting death data to the differential equation curves.

The future direction for this project is to ascertain and correct the actual cause of the convergence failure. The following steps include running an SIRD model for each of the 50 states and joining them into a “master model” for the whole of the United States, as well as creating a data retrieval function to update the data automatically to keep the model current. If these additions are be achieved, then creating an intuitive interface through R Shiny and expanding the model to include things like quarantines and vaccination will be explored.

For the time being, this project has been paused for a lack of ability to commit the necessary time the project deserves. 


