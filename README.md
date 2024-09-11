# Take-Home-Test

## Estimating Crowd Size on Bridge using Traditional Computer Vision Techniques

#### The proposed solution processes the video frame by frame to estimate the number of people on the bridge. For each frame, the background will be removed to isolate the bridge or road area, ensuring that only relevant regions are considered for analysis. Due to the nature of the footage (drone footage), where individuals are not distinctly identifiable, traditional object detection techniques may not be effective. Blob Detection is used to identify and estimate the number of people in each frame.

#### Now for the 2nd part of the solution, how do we ensure that the same person is not being counted multiple times as we process subsequent frames? To prevent counting the same person multiple times across consecutive frames, a centroid tracking algorithm is used. For each frame, when a person is detected, the algorithm checks if a person was also detected in the previous frame within the same pixel neighborhood (e.g., within a 200-pixel radius). If so, it is assumed to be the same person, and they are not counted again. If no match is found in the previous frame, the person is counted as a new individual. 

#### Reasons for thresholds:
#### There are around 210,000 pixels in each frame. it is safe to assume that a person occupies 100 pixels. 

#### (Actual detection screenshots included, people are detected and marked with a green circle.)


![image](https://github.com/user-attachments/assets/f5b6c2ca-a23c-4ffe-9c36-0d035f190548)

![image](https://github.com/user-attachments/assets/d9ce65f9-e00a-440c-aab5-cf300e58ef7b)

## Validation

#### One way to validate the solution is by comparing consecutive frames to ensure consistency in the number of people detected. In an accurate method or model, the number of people identified in two successive frames should remain relatively stable, without significant fluctuations.

## Alternative Solutions

#### Another idea I considered was converting the side-view footage to a bird's-eye view. However, this would require precise knowledge of the coordinates of the region of interest (the bridge or road). Implementing this would likely involve deep learning-based segmentation techniques to accurately identify the area. Since the assessment focused on using traditional computer vision techniques, this approach may not be suitable. Additionally, perspective warping poses the risk of losing valuable information, as parts of the image may be cropped during the transformation.

#### There are also density-based methods to estimate crowd sizes in frames. However, these techniques typically rely on deep learning models that must be fine-tuned to the specific use case using images from a similar distribution.

#### I had also considered using the SORT algorithm (https://github.com/abewley/sort) for object tracking. However, I was unable to configure and implement it on my local machine due to time constraints.

#### Other common pretrained model used for object detection and tracking, will not be suitale for this task as the people in the footage look extremely small, which is very different from the data these models were trained on. Hence it wont be able to identify people from Drone Footage.

