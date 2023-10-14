# Project 1: Aerodynamic design optimization of rear body shapes of a sedan for drag reduction.
* This is a surrogate tool which uses aerodynamic loadcase datasets to perform predictive analytics for product optimization.
* Over 1000 datasets were scraped from server & preprocessed.
* Various machine learning tools applied to perform analysis.
* Accuracy for all analysis were compared to get the best methodology.

## Background
Aerodynamic drag is the resistance offered by incoming air flow over an object under motion. Formula to equate this resistive force: \
![](/images/Image_2.JPG)

It is evident from above formula that the resistive force increases exponentially with an increase in velocity.
Aerodynamic drag force is one of the major contibutors in motion resistance & a lot of fuel energy is converted to overcome this.
And the the resistive force is directly proportional to the coefficient of drag (Cd) which is a shape function of the object under motion.

A sedan (example: as shown below)is typically known for its stylish design & minimum drag force.
However, the rear end shape of a sendan is crutial for its wake region.
Optimizing the shape may lead to minimizing the coefficient of drag & hence improve fuel efficiency. \
![](/images/Image_3.JPG)

## Problem Statement
To minimize drag, i.e. Cd, 4 paramters are being considered to optimize the sedan's rear body shape as shown below: \
![](/images/Image_1.JPG)

## Dataset
The physics was built using a simulation tool. The virtual car model was given as input to this tool & the simulation was run for 23000 iterations.
Following parameters were obtained as output in CSV (Comma Separated Values) format: \
Iteration, Continuity, X-momentum, Y-momentum, Z-momentun, Cd. \
For each simulation the Cd average of last 14000 iterations were to be considered as the Cd value of that simulation, as shown in below figure. \
![](/images/Image_4.JPG) \
\
Similar simulations, which were performed & already present in the server space, were collected itnto the database folder. \
1000 such CSV files were collected, each having a unique combination of L<sub>T</sub>, &theta;$<sub>T</sub>, L<sub>D</sub> and &theta;$<sub>D</sub>. 

## Database Management
Using MYSQL following tasks were performed: 
1. From each simulation's 23000 iterations, average values of last 14000 iterations' Cd values were calculated. 
2. A new table was created which stored Cd averaged values of 1000 simulations.
3. This table is then joined with the 'design_of_experiment table' and stored as 'result_summary' table.

The code snapshot used to perform these tasks is shown below: \
![](/images/Image_5.jpg) \
Finally, the 'result_ummary' table contained following attributes: \
model_id, trunk_length, trunk_angle, bumper_length, bumper_angle, cd_value 

## Data Analytics
