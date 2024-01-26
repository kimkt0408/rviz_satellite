# rviz_satellite - Offline Satellite Image Visualization

This document serves as a manual for setting up and using the `rviz_satellite` package for offline visualization of satellite images in RViz alongside other outputs.


## Initial Setup

### Configuring `demo.gps`
To set the initial map frame, edit the following parameters in `demo.gps`:
- `latitude`
- `longitude`
- `altitude`
- `position_covariance`
- `position_covariance_type`

*Note: Copy and Paste the parameters from `rostopic echo /gps/fix`*

### Using Google Maps
To use Google Maps for satellite imagery:
1. **Request an Access Token** for Google Maps. Use the following command to access the tiles:
```
http://localhost:8080/wmts/gm_layer/gm_grid/{z}/{x}/{y}.png
```


## Launching rviz_satellite

To launch the rviz_satellite visualization tool, use the command:
```
roslaunch rviz_satellite demo_utm.launch
```


## How to Use Satellite Images

### In Real-Time
- **No Image Map Visualization**: In real-time applications, there is no need to visualize the image map. Computational efficiency is not good to visualize with on-board computer.

### Offline Visualization
- **Image Map in RViz**: For offline purposes, visualize the image map in RViz for more detailed analysis.

## Current status on the applications

- **P-AgSLAM Output**: The following outputs from P-AgSLAM can be visualized in RViz along with a tiled map for comprehensive spatial understanding:
  - `/gtsam/trajectory`: P-AgSLAM with RTK GPS integration by GTSAM
  - `/pagslam/debug/original_trajectory`: WO+IMU without RTK GPS integration by GTSAM
  - `/pagslam/debug/trajectory`: P-AgSLAM without RTK GPS integration by GTSAM


## Unsolved problems and Notes

- **Real-Time Visualization Limitations**: Currently, the real-time visualization does not include image maps, which might be crucial for certain applications.
- **Trajectory Merging**: One unsolved problem is how to effectively merge all baseline trajectories for a unified view. (rviz? or matlab?)
- **Additional Data Integration**: Integrating other outputs with GPS data for enhanced visualization in RViz remains a challenge, especially in terms of synchronizing different data streams and ensuring spatial and temporal accuracy.


## Additional Resources

- **Google Maps in MapViz**: For detailed descriptions of using Google Maps in MapViz, visit the GitHub repository:
  [MapViz-Tile-Map-Google-Maps-Satellite](https://github.com/danielsnider/MapViz-Tile-Map-Google-Maps-Satellite).

- **RViz Satellite Package**: For a detailed description and options of the `rviz_satellite` package, read the README of the package:
  [rviz_satellite.md](rviz_satellite.md)

---

*Note: This documentation is intended as a manual for the setup and usage of package `rviz_satellite`.*
