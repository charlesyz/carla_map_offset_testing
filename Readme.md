# Carla Map Offset Testing

Working Jupyter Notebook for debugging an issue I had at Watonomous with coordinates of a map in CARLA not reflecting coordinates in real life. 

Preserved for future reference

## Description of the Bug

We created a map of Michigan's MCity Test Facility in CARLA using RoadRunner. The source data for the map is HERE HDM Data provided by SAE.

We are using CARLA as a full software in the loop simulator. In the map, we noticed that our position in CARLA does not reflect our position on our HD map.

Our HERE HD map consists of lat long coordinates that are projected into UTM by the Lanelet2 Library (which internally uses geographiclib).  

CARLA and RoadRunner use XY coordinates in UTM (meters) with some origin point specified in an XODR file created by RoadRunner.

These coordinate systems do not seem to line up.

## Solution to the bug

Create a Lanelet2 Projector that follows CARLA's scuffed implementation of a WGS84 to UTM projection. As shown in the notebook, this projection will make our projected map line up with CARLA.

## Description of Files

