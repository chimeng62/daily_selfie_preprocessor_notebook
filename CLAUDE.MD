Facial Alignment Pipeline for an Aging Timelapse
This document outlines a robust pipeline for preparing a series of selfies for a seamless and high-quality aging timelapse video. The primary goal is to normalize the scale, rotation, and position of faces across multiple photos, ensuring a smooth transition between frames.

The Problem
A key challenge in creating a self-portrait timelapse is the inherent inconsistency of daily photos. Selfies taken over time will vary in:

Scale: The face may appear closer or farther away in different photos.

Rotation: The head may be tilted or angled differently.

Position: The face may not be perfectly centered in every frame.


The Proposed Pipeline
Rather than manually aligning each image or using a single "ideal" photo as a reference, this pipeline uses a data-driven approach by aligning all images to a calculated "average" face.

Step 1: Input
The pipeline begins with a collection of selfies, organized chronologically. These images serve as the raw input for the process.

Step 2: Face Detection
For each image, a face detection model is used to identify the bounding box of the face. This isolates the region of interest for the next steps.

Step 3: Facial Landmark Detection
Within the detected face, a facial landmark detection model pinpoints key features, such as the corners of the eyes, the tip of the nose, and the corners of the mouth. These landmark coordinates are the most critical data points for the alignment process.

Step 4: Calculate the "Average Face"
Before alignment, the coordinates of all landmarks from every single photo are collected. The pipeline then computes the average position for each landmark across the entire dataset. This creates a stable, consistent target geometry that is representative of the whole collection.

Step 5: Alignment and Normalization
This is the core of the pipeline. For each individual selfie, a geometric transformation (rotation, scaling, and translation) is calculated to align its landmarks to the corresponding average landmark positions. This transformation is then applied to the entire image.

Step 6: Output
The output is a new series of images, all with faces that are in the exact same position, scale, and rotation. These normalized images are now ready to be stitched together into a smooth, professional-looking timelapse video.



## Directory

input: selfie images
output: eye-aligned selfies 
input folder: source_selfies 
output folder: output_selfies

