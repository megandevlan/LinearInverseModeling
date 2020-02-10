# LinearInverseModeling
Scripts to build a linear inverse model (LIM) based on an input pickle file.

These scripts were initially created for analysis carried out in Fowler and Penland (2020; in prep): "Predictability of soil moisture in Northern California." They have, however, been modified to be as versatile as possible for any given user (at least in the case of LinearInverseModel.ipynb). 

Scripts: 
1. <b>PrepareSoilData.ipynb</b>: This case-specific file prepares data for input to the linear inverse model script. In our case, this requires combining data from multiple files into a single array, removing the mean from each soil observing station, computing and removing the average annual cycle from each, taking their z-scores, and finally carrying out a linear regression to isolate only residual soil temperature. 
