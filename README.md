# ViChan-Dataset
A dataset generation framework for vision-aided wireless channel estimation
#  ViChan Dataset

**ViChan** is a paired **image–channel dataset** developed for research on **vision-aided** and **environment-aware wireless communications**.  
It provides one-to-one correspondences between **radio channel information** (simulated via MATLAB ray-tracing) and **top-view environment images** (captured from Google Earth Pro).  
The dataset enables deep learning models to learn correlations between environmental visual features and wireless channel characteristics, supporting 6G-oriented intelligent communication systems.

---

##  Dataset Structure
The **ViChan Dataset** is organized in a hierarchical structure to ensure modularity, clarity, and scalability for future extensions to multiple cities or environments.

ViChan-Dataset/ │ ├── README.md # Project overview, usage, and citation ├── LICENSE # Open-source license (MIT recommended) ├── metadata.json # Global metadata (city, frequency, ray-tracing parameters, etc.) │ ├── /docs/ # Documentation and illustrations │ ├── framework_overview.png │ ├── sample_pair.png │ └── dataset_description.pdf │ ├── /data/ # Main dataset folder │ ├── /manhattan/ # Example city or scenario │ │ ├── osm_building.osm # 3D building data (from OpenStreetMap) │ │ ├── txrx_coordinates.csv # List of transmitter–receiver coordinate pairs │ │ ├── /samples/ # Folder containing all paired samples │ │ │ ├── /tx01_rx001/ # One Tx–Rx pair folder │ │ │ │ ├── tx01_rx001.csv # Ray-traced channel data │ │ │ │ ├── tx01_rx001.jpg # Environment image (top-view) │ │ │ │ ├── tx01_rx001.json # Metadata (frequency, reflections, materials, etc.) │ │ │ │ └── ... │ │ │ ├── /tx01_rx002/ │ │ │ ├── /tx02_rx001/ │ │ │ └── ... │ │ └── index.csv # Mapping table (TxRx ID ↔ filenames) │ │ │ ├── /hongkong/ │ │ ├── osm_building.osm │ │ ├── txrx_coordinates.csv │ │ ├── /samples/ │ │ │ ├── /tx01_rx001/ │ │ │ │ ├── tx01_rx001.csv │ │ │ │ ├── tx01_rx001.jpg │ │ │ │ ├── tx01_rx001.json │ │ │ │ └── ... │ │ └── index.csv │ │ │ └── ... │ ├── /scripts/ # Data generation and organization scripts │ ├── generate_channel_data.m # MATLAB ray-tracing simulation │ ├── capture_images.kml # Google Earth automated capture script │ ├── build_index.py # Generate index or hash-based lookup │ └── merge_dataset.py # Merge images and channel data │ └── /examples/ # Example usage and demos ├── load_vichan_data.ipynb # Python example: loading and visualization ├── visualize_pairs.py └── train_model_demo.py # Example ML training script
