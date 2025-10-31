# ViChan-Dataset
A dataset generation framework for vision-aided wireless channel estimation
#  ViChan Dataset

**ViChan** is a paired **image–channel dataset** developed for research on **vision-aided** and **environment-aware wireless communications**.  
It provides one-to-one correspondences between **radio channel information** (simulated via MATLAB ray-tracing) and **top-view environment images** (captured from Google Earth Pro).  
The dataset enables deep learning models to learn correlations between environmental visual features and wireless channel characteristics, supporting 6G-oriented intelligent communication systems.

---

##  Dataset Structure
# -----------------------------------

The four scenarions are zipped into one directory, and it is structured as follows:

    ViChan-Dataset
    |
    |- README.md
    |- LICENSE
    |- docs
    |    |
    |    |- framework_overview.png
    |    |- dataset_description.pdf
    |
    |- data
    |    |
    |    |- manhattan
    |    |     |
    |    |     |- osm_building.osm
    |    |     |- txrx_coordinates.csv
    |    |     |
    |    |     |- samples
    |    |     |     |
    |    |     |     |- sample_40.701568_-74.012196
    |    |     |     |     |- channel.csv
    |    |     |     |     |- image.jpg
    |    |     |     |     |- metadata.json
    |    |     |     |
    |    |     |     |- sample_40.709866_-74.012831
    |    |     |     |     |- channel.csv
    |    |     |     |     |- image.jpg
    |    |     |     |     |- metadata.json
    |    |     |     |
    |    |     |     |- ...
    |    |     |
    |    |
    |    |- hongkong
    |    |     |
    |    |     |- osm_building.osm
    |    |     |- txrx_coordinates.csv
    |    |     |
    |    |     |- samples
    |    |     |     |
    |    |     |     |- sample_tx01_rx001
    |    |     |     |     |- channel.csv
    |    |     |     |     |- image.jpg
    |    |     |     |     |- metadata.json
    |    |     |     |
    |    |     |     |- ...
    |    |     |- ...
    |    |- ...
    |


---

##  Data Description

Each **sample folder** corresponds to a transmitter–receiver (\`Tx–Rx\`) pair and contains three synchronized files:

| File | Description |
|------|--------------|
| `channel.csv` | Ray-traced wireless channel data (path loss, delay, phase shift, angles, etc.) |
| `image.jpg` | Top-view RGB image centered at the receiver (from Google Earth Pro) |
| `metadata.json` | Scene-level metadata (Tx/Rx coordinates, frequency, material, reflection order, etc.) |

All filenames are indexed by coordinates or Tx–Rx IDs, enabling one-to-one correspondence between visual and wireless modalities.  
The dataset uses 3D building geometry from **OpenStreetMap (OSM)** or MATLAB’s built-in Manhattan model for environment construction.

---

##  Data Generation Pipeline

1. **Wireless Channel Simulation (MATLAB)**
   ```matlab
   viewer = siteviewer("Buildings","Manhattan.osm");
   run("scripts/generate_channel_data.m");
   Generates channel.csv files using ray-tracing under urban propagation conditions.

2. **Environment Image Capture (Google Earth Pro)**

   Load the capture_images.kml file.
   Fix the camera altitude at 200 m, tilt = 0°, and roll = 0° for consistent top views.
   Capture one image per Tx–Rx pair and save as .jpg.



##  Research Applications
(1) Vision-Aided Channel Estimation and Prediction

Use visual information to infer radio propagation properties, reduce pilot overhead, and enhance beam selection in 5G/6G systems.

(2) Extended Use Cases

Site-specific wireless network planning

Radio scene classification & semantic sensing

Environment-aware communication system design

Digital twin and multi-modal simulation


##  Citation

@dataset{liu2025vichan,
  author    = {Zhaojun Liu},
  title     = {ViChan: A Dataset Generation Framework for Vision-Aided Channel Estimation},
  year      = {2025},
  url       = {https://github.com/2019V/ViChan-Dataset}
}
