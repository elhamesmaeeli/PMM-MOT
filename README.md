# Adaptive Probabilistic Multi-Model Framework for Robust 3D Multi-Object Tracking Under Uncertainty  Tracking
3D multi-object tracking is a crucial task for intelligent navigation systems and autonomous vehicles, 
enabling continuous localization and re-identification of surrounding objects. 
Current methods often rely on simple motion models like constant velocity and constant turn for trajectory prediction. 
However, these models struggle in uncertain environments where objects may perform abrupt maneuvers 
due to various factors such as collision avoidance, curiosity-driven exploration, or scene dynamics. 
To address this challenge, we propose a dynamic probabilistic multi-model framework 
that leverages multiple parallel motion models for enhanced prediction accuracy, 
considering potential object maneuvers. 
Our framework introduces two novel motion models based on a learned probabilistic multi-category deviation angle. 
Combined with the constant velocity model, these yield three trajectory predictions, each assigned a probability of occurrence. 
We utilize a machine learning model based on logistic regression to estimate 
the probability of each prediction according to the object's momentum. 
Additionally, we introduce two probabilistic cost functions for updating trajectories during 
a two-stage data association process, prioritizing predictions with higher probabilities. 
Experiments on the nuScenes dataset demonstrate our framework's superior performance, 
achieving an average multi-object tracking accuracy of **78.4%**, surpassing state-of-the-art trackers.

![PMM-MOT poster](images/PMM-MOT-Poster.png)

## PMM-MOT Architecture
PMM-MOT is divided into four separate modules: multi-modal 3D object detection (MM-ODM), probabilistic multi-motion trajectory prediction (PMM-TPM), probabilistic two-stage data association (PTS-DAM), and trajectory management

![PMM-MOT main architecture at frame t](images/PMM-MOT-Architecture.png)

## Benchmark Result
### The PMM-MOT results on nuScenes validation set:
| Detector                    | Sensor Modality | AMOTA    | AMOTP    | IDS     |
| :---------------------------: | :---------------: | :--------: | :--------: | ------- |
| LargeKernel3D-L             | LiDAR           | 74.8     | 54.9     | 263     |
| CenterPoint & Cascade R-CNN | Camera + LiDAR  | 76.3     | 54.7     | 213     |
| BEVFusion                   | Camera + LiDAR  | 76.9     | 56.2     | 219     |
| LargeKernel3D               | Camera + LiDAR  | **78.4** | **54.4** | **207** |


## Visualization of Results
Visualization of PMM-MOT result at sene-0998 (frame 4) of nuScenes dataset

![The result of CV and CT model](images/Visualization2.png)

![The result of CV and CT model](images/Visualization1.png)

# Resources for calculating the average mass of objects
The table below indicates the resources for calculating the average mass of each category of objects:

| Category   | Average Mass (kg)     | References                                                                                                                                                                                                                                                                               |
| :----------: | :-----------------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pedestrian | 70                | 1: [https://www.cdc.gov/nchs/data/series/sr_03/sr03-046-508.pdf](https://www.cdc.gov/nchs/data/series/sr_03/sr03-046-508.pdf)<br>2: [https://en.wikipedia.org/wiki/Human_body_weight](https://en.wikipedia.org/wiki/Human_body_weight)                                                   |
| Bicycle    | 80                | [https://www.bikesales.com.au/](https://www.bikesales.com.au/)                                                                                                                                                                                                                           |
| Motorcycle | 200               | [https://www.cycleworld.com/](https://www.cycleworld.com/)                                                                                                                                                                                                                               |
| Car        | 1,500             | [The 2020 EPA Automotive Trends Report](https://www.epa.gov/sites/default/files/2021-01/documents/420r21003.pdf)                                                                                                                                                                         |
| Bus        | 12,000            | [The 2020 EPA Automotive Trends Report](https://www.epa.gov/sites/default/files/2021-01/documents/420r21003.pdf)                                                                                                                                                                         |
| Trailer    | 1,500             | 1: [https://www.amazon.com/Driving-Instructors-Handbook-John-Miller/dp/0749483938](https://www.amazon.com/Driving-Instructors-Handbook-John-Miller/dp/0749483938)<br>2: [The 2020 EPA Automotive Trends Report](https://www.epa.gov/sites/default/files/2021-01/documents/420r21003.pdf) |
| Truck      | 9,000             | 1: [https://www.amazon.com/Driving-Instructors-Handbook-John-Miller/dp/0749483938](https://www.amazon.com/Driving-Instructors-Handbook-John-Miller/dp/0749483938)<br>2: [The 2020 EPA Automotive Trends Report](https://www.epa.gov/sites/default/files/2021-01/documents/420r21003.pdf) |
