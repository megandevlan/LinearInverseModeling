# LinearInverseModeling
Scripts to build a linear inverse model (LIM) based on an input pickle file.

These scripts were initially created for analysis carried out in Fowler and Penland (2020; in prep): "Predictability of soil moisture in Northern California." They have, however, been modified to be as versatile as possible for any given user (at least in the case of LinearInverseModel.ipynb). 

Scripts: 
1. <b>PrepareSoilData.ipynb</b>: This case-specific file prepares data for input to the linear inverse model script. In our case, this requires combining data from multiple files into a single array, removing the mean from each soil observing station, computing and removing the average annual cycle from each, taking their z-scores, and finally carrying out a linear regression to isolate only residual soil temperature. The steps *you* take to prepare your own data will almost certainly differ, but this is provided as an example. The key steps to preparing your own data will be to center the data and remove the annual cycle (how you do this is up to you). Then save that data as a pickle file (https://wiki.python.org/moin/UsingPickle), with an array of dimensions [nData, nTime]. 

2. <b>LinearInverseModel.ipynb</b>: This is the crux of the work. Here, a linear inverse model is built based on a user-supplied pickle file. Other inputs required are a list of stationIDs (i.e., what you would like each data point to be referred to) and a value for tau_0, the lag at which LIM will estimate its parameters. The LIM is built in a step-by-step process here, with a key section (Section #5) devoted to testing the validity of applying LIM. *This is a critical piece to consider.* If your data gives rise to Nyquist modes, the tau test is clearly failed, or if the eigenvalues of Q are not all positive, LIM is not a valid choice for your needs. 

3. <b>MSE_SoilMoistureHindcasts.ipynb</b>: This script is as generic as possible, though it is noted throughout that you may want to change a number of options. The overall purpose here is to compare the mean squared error of LIM-generated hindcasts (based on results from the above script) to errors associated with an AR1 process. This is also where we define "forecasts of opportunity" based on how strong the projection of the optimal structure is on initial conditions. 

