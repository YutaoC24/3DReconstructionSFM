### Project Description ###
This python project implements 3D reconstruction of the object from multiple images using structure from motion(SFM) method. 

### Data and file overview ###
This directory includes dataset folder: house. 
	house folder includes 10 grey-scale photos of a model house taken by Visual Geometry Group, University of Oxford.
3DReconstructionLazyPipeLine.ipynb and 3DReconstructionHardPipeLine.ipynb are the two python notebook files for the implementation of SFM method.
	3DReconstructionLazyPipeLine.ipynb takes the 10 images from house folder to compute a visualized 3D point cloud.
	3DReconstructionHardPipeLine.ipynb takes the images from customized folder to compute a visualized 3D point cloud.
	One is welcome to import customized photos to test the implementation.

### Details ###
3DReconstructionLazyPipeLine.ipynb is applicable to images with known projection matrices.
3DReconstructionHardPipeLine.ipynb is applicable to images with known camera intrinsic matrices.
Both pipelines firstly use the SIFT algorithm from OpenCV as feature detector to extract possible matches, with RANSAC outlier rejection.
LazyPipeLine then constructs point cloud with triangulation (assuming the projection matrices are given) and converts the point cloud to a .ply binary file stored at desired location. It then constructs a 3D surface mesh with Poisson Mesh reconstruction and stores the result as a .ply binary file at desired location.
HardPipeLine goes through a similar post-production process except that it computes the fundamental matrix with RANSAC outlier rejection and calculates the essential matrix. The camera projection matrix is computed by getting the dot product of the camera pose matrix and the intrinsic matrix. The procedures afterwards remain the same as LazyPipeLine.

### Usage ###
If one desires to use the given data-set, simply run through every cell to view the visualized 3D point cloud at the end, with the platform provided by Plotly.
Parameters in RANSAC, directories and filenames are all variables that could be changed to fulfill user's purpose. 
Note that when custmized photos are imported to the HardPipeLine, the camera intrinsic matrix need to be manually changed and set.
