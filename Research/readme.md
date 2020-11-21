# Research README

<<<<<<< HEAD
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/Ron-Zehavi/anomalies-detection/HEAD)

=======
>>>>>>> origin/main
### Pre-Processing 
Please run https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Research/EDA.ipynb to see the EDA.

### Json Files
In https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Research/create_sector_and_authority_jsons.ipynb you need to run the file, in order to get update for these 2 files:
1. water_authority.json - file containing a dictionary of all points ID by water authorities
<<<<<<< HEAD
2. sectors.json - file containing a dictionary of all points ID by sectors

=======
https://github.com/Ron-Zehavi/anomalies-detection/blob/main/water_authority.json
2. sectors.json - file containing a dictionary of all points ID by sectors
https://github.com/Ron-Zehavi/anomalies-detection/blob/main/sectors.json
>>>>>>> origin/main

### Sectorial data
You can aggregates the data of a sector in authority level, and saves it as pickle file. 

In https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Research/create_sectorial_data.ipynb you need to enter:
* `RESAMPLE` - the smallest time unit for the plots
* `WINDOW` - window size
* `THRESHOLD` - the top % of most similar motifs
* `NODE` - point ID
* `SECTOR` - sector name
 And run the file.

### Sectorial Mtrix Profile
This file create matrix profile of a sector in authority level, and saves it as pickle file.

In https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Research/create_sectorial_matrix_profile.ipynb you need to enter:
* `FILE_NAME` = name of the sector pickle file
* `ANOMALY_SCORE` - anomaly score = -0.25
* `WINDOW` - window size
