# SpaceTimeCube

This repository contains the sample data and code of the 'Space Time Cube' plugin of QGIS 3.x.
* The URL of the plugin: <a href="https://plugins.qgis.org/plugins/space_time_cube/" target="_blank">`https://plugins.qgis.org/plugins/space_time_cube/`</a>
* Video tutorial: <a href="https://www.youtube.com/watch?v=Tcdvlk_NS8w&feature=youtu.be" target="_blank">`https://www.youtube.com/watch?v=Tcdvlk_NS8w&feature=youtu.be`</a>  

The main purpose of the plugin is the detection of hot spots localised in space and time using two different statistics: i) Getis-Ord $G_i*$ and ii) local Moran's I.

The plugin requires the following inputs:
* **Input data:** the space-time point data set available in the QGIS layer panel.
* **Weight field:** whether a weight is assigned to the points. One of the attributes of the data could be selected.
* **Cube dimensions:**
 * The first option *size* allows the selection of the number of cells for each axis.
 * The second option *internal* allows the user to specify the approximated length of a cell.

---
**Example**

Assume maximum distance along the *x*-axis to be 1248 metres.

1. **Size** parameter $\eta_x = 50$: The length of a cell on the *x*-axis would be 24.96 metres.
2. **Interval** parameter $\Delta x = 100$ metres, then there would be 12 cells on the *x*- axis each having a length of 104 metres. This approximation was realised in order to minimise the edge effect.  
---

* **Select time field:** The user can select the time field based on various different representations.
* **Create tiff files:** This optional field creates tiff files for each time slice.
* **Statistic Method:** Determines the hot spot detection method.
* **Aggregation Method:** How the points inside a cell are aggregated. If no weight is assigned, then ***Sum*** should be used. If there is a weight, then all three options are viable.

<p align="center">
  <img width="350" src="img/1_create_cube.jpg">
</p>

The second tab of the plugin allows

The plugin identifies the Minimum Spanning Tree (MST) of geographical inputs. Three different ways to determine costs of edges are considered, which constitute the tabs of the plugin:
1. **Vector**: Provided by the given input linestring.
2. **Automatic**: Obtained automatically based on the input shapefile. Delaunay Triangulation is used to obtain the edges, and Euclidean distance is used to determine the costs.
3. **Raster**: Both raster and vector data are used to estimate the costs of edges. In all of the cost estimation methods, there is an optional barrier (obstacle) input, which makes sure that no edge in MST intersects with a barrier provided as a linestring. To obtain reliable results, all of the inputs must be in the same coordinate system.

Raster data can be downloaded from: <a href="http://yunus.hacettepe.edu.tr/~banbar/mst_raster.zip" target="_blank">`http://yunus.hacettepe.edu.tr/~banbar/mst_raster.zip`</a>

<p align="center">
  <img width="600" src="images/flowchart.jpg">
</p>

The OSGeo functionalities used within the plugin are described [here](https://raw.githubusercontent.com/banbar/Minimum_Spanning_Tree_QGIS/431cf56ff2e6bc088d7adceac0c8923f849cfd11/img/code%20diagram_explanations.svg).
