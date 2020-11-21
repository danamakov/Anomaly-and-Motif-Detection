# Anomaly and Motif Detection

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/Ron-Zehavi/anomalies-detection/HEAD)


### Installation

All requirements can be found in `requirements.txt`, for easy installation:

```sh
$ pip install requirements.txt
```

In order to use the files to create new data or plots, you need to have a key and password ("secret") of Kando developer, and store it in key.json file. You need to enter:
* `KEY` - your key
* `SECRET` - your password

And run the file.

### Pre-Processing 
Please use https://github.com/Ron-Zehavi/anomalies-detection/blob/main/save_points_matrix_profiles.ipynb to calculate and save the data for every point belongs to a chosen water authority. You need to enter:
* `RESAMPLE` - the smallest time unit for the plots
* `WINDOW` - window size
* `WATER_AUTHORITY_NUM` - water authority ID
* `START` - start date as timestamp

And run the file.

### Motifs
A motif is a repeated pattern in a time series. The Matrix Profile stores the distances in Euclidean space.
> The algorithms that compute the Matrix Profile use a sliding window approach. With a window size of m, the algorithm:
1. Computes the distances for the windowed sub-sequence against the entire time series
2. Sets an exclusion zone to ignore trivial matches
3. Updates the distance profile with the minimal values
4. Sets the first nearest-neighbor index

As Tyler Marrs write on https://towardsdatascience.com/introduction-to-matrix-profiles-5568f3375d90 .

In https://github.com/Ron-Zehavi/anomalies-detection/blob/main/plot_motifs.ipynb you need to enter: 
* `RESAMPLE` - the smallest time unit for the plots
* `WINDOW` - window size
* `THRESHOLD` - the top % of most similar motifs 
* `NODE` - point ID
* `START` - start date as timestamp

And run the file.

You can see interactive plot of motifs on a map in the https://github.com/Ron-Zehavi/anomalies-detection/blob/main/plot_map.ipynb you need to enter:
* `FILE_NAME` - CSV file containing motif information of the water authority
* `RESAMPLE` - the smallest time unit for the plots

 And run the file.

You can use the file https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Map/create_coordinates_df_csv.ipynb to create more CSV files containing motif information of other water authorities. You need to enter:
* `WATER_AUTHORITY_NUM` - water authority ID
* `START` - start date as timestamp

And run the file.

### Anomalies
In the next section we find anomalies, through anomalies detection we believe more contamination events can be revealed. Therefore, we built a tool for the development team that allows finding anomalies according to 4 different methods.

In https://github.com/Ron-Zehavi/anomalies-detection/blob/main/plot_anomalies.ipynb you need to enter:
* `NODE` - point ID

And run the file.

In https://github.com/Ron-Zehavi/anomalies-detection/blob/main/plot_anomalies_3D.ipynb you need to enter:
* `NODE` - point ID
* `WINDOW` - window size

And run the file.

![alt text](https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Readme_files/eif.png)
![alt text](https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Readme_files/iso.png)
![alt text](https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Readme_files/mf.png)
![alt text](https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Readme_files/vae.png)

Now we are looking on screenshots from the tool that show the information from point 883 in Gichon, at the same time - from 2020. The big blue cloud is made from all the normal points and the stars represent points that detected as anomalies by the different methods.

We first used a classic machine learning method to find anomalies called `Isolation Forest` and the more advanced version of it called `Extended Isolation Forest`. For more information check https://github.com/sahandha/eif.

The 2 methods are able to detect points that are isolated from the cloud, so sometimes there are events that do not necessarily pass the threshold but are clearly not part of the normal activity of the point, and we can detect them with this way.

Second, we used the `Matrix Profile` method to find anomalies, since the method use the form of the information we can again find abnormal behaviours. 

And finally, we applied deep learning - `Auto Encoder` - the computer doesn’t work with isolated data or unique patterns, rather it learns the best set of rules that define each and every point, and detect as anomalies as the points that don’t fit into this set of rules. We believe that this last method will be the best to find more interesting cases like contamination events. 

Moreover, you can use https://github.com/Ron-Zehavi/anomalies-detection/blob/main/Data_with_anomalies/create_anomalies_df.ipynb to run the same process for other points. You nedd to enter:
* `WATER_AUTHORITY_NUM` - water authority ID
* `WINDOW` - window size

And run the file.
