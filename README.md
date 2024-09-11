# Take-Home-Test

## Estimating Crowd Size on Bridge using Traditional Computer Vision Techniques

#### The proposed solution processes the video frame by frame to estimate the number of people on the bridge. For each frame, the background will be removed to isolate the bridge or road area, ensuring that only relevant regions are considered for analysis. Due to the nature of the footage (drone footage), where individuals are not distinctly identifiable, traditional object detection techniques may not be effective. Blob Detection is used to identify and estimate the number of people in each frame.

#### Now for the 2nd part of the solution, how do we ensure that the same person is not being counted multiple times as we process subsequent frames? To prevent counting the same person multiple times across consecutive frames, a centroid tracking algorithm is used. For each frame, when a person is detected, the algorithm checks if a person was also detected in the previous frame within the same pixel neighborhood (e.g., within a 50-pixel radius). If so, it is assumed to be the same person, and they are not counted again. If no match is found in the previous frame, the person is counted as a new individual. 

#### (Actual detection screenshots included, people are detected and marked with a green circle.)

![image.png](attachment:6aaac527-a444-40b6-870e-3491637d6f87.png)

