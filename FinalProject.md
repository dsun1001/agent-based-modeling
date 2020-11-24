## Final Project

### Gravity Model of London

In the first part of this project, we followed a [guide by Adam Dennett](https://rpubs.com/adam_dennett/257231) to practice creating a gravity model. Gravity models as applied to migration use population sizes and distances between each location as push and pull factors, and can be expanded upon by adding in additional characteristics of the locations. The end result is a model of migration that can predict human behavior and help to provide a better understanding of situations. From Garcia et al (2015), they found that gravity models could explain up to 87% of internal migration, and demonstrated that models could predict flow even in regions where data is sparse. 

As we can see, gravity models are powerful tools. Continuing to learn them via the Dennett London example, we first pull in spatial data about London. Using the spatial data, we can calculate a distance matrix and also pull in some data about the flow of the population. Now that we have the data that we need, how do we implement a gravity model? 

<a href="https://www.codecogs.com/eqnedit.php?latex=MIG_{ij}=\frac{p^{a}_{i}\cdot&space;p^{b}_{j}}{d^{c}_{ij}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?MIG_{ij}=\frac{p^{a}_{i}\cdot&space;p^{b}_{j}}{d^{c}_{ij}}" title="MIG_{ij}=\frac{p^{a}_{i}\cdot p^{b}_{j}}{d^{c}_{ij}}" /></a>

According to Garcia et al, this is the modern from of the gravity model. The flux of migration between two places, *i* and *j*, is proportional to their masses (populations) and inversely proportial to the distance between them, and each of the components has an exponent that controls how strong that interaction is. 

With our London model, we follow an approach that first estimates some values for the gracity model to use when predicting flow, and then look at error values to assess how well we're estimating our parameters. However, in order to find the best parameters for us to use, we can take the logarithms of our gravity model in order to create a regression model. However, rather than using a log-normal regression model, in this case we use a Poisson regression model. This is because with migration, we need to deal with non-negative integer counts. After we have our Poisson regression model, we can use it to estimate our parameters. Once we have the new parameters, we can once again estimate our flow estimates, and it looks like this. 

![](london_grav.png)

### Bendje

[WorldPop Migration Flow](https://www.worldpop.org/geodata/summary?id=1281)
[WorldPop Night-time Lights](https://www.worldpop.org/geodata/summary?id=18614)
