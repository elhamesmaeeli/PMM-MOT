# PMM-MOT: A Probabilistic Multi-Motion Framework for 3D Multi-Object Tracking
3D Multi-Object Tracking (MOT) is a computer vision task that plays a vital role in intelligent navigation systems, primarily due to its ability for continuous localization and Re-Identification (Re-ID) of surrounding objects. Existing methods rely solely on a simple motion model (e.g., Constant Velocity (CV)) to predict the subsequent state of each trajectory. However, in the face of uncertain environmental conditions, objects may alter their motion models and perform abrupt maneuvers influenced by factors like avoiding collision, curiosity-driven exploration, and scene dynamics, which hinder the effectiveness of such methods. As such, a Probabilistic Multi-Motion 3D MOT (PMM-MOT) framework is proposed, which employs multiple parallel motion models to enhance prediction accuracy by considering potential object maneuvers. To achieve this, PMM-MOT introduces two new motion models, Left and Right Probabilistic CV (LPCV and RPCV), which intelligently restrict the object maneuvers within a confined dynamic space. Each prediction comes with its probability of occurrence, which must be considered during the association process. Toward this end, PMM-MOT introduces a novel machine learning model built on logistic regression, which can be trained on various datasets to estimate the probability of each prediction based on the object's momentum. Additionally, two new probabilistic cost functions are introduced to update trajectories using detections through a two-stage data association process, prioritizing high probability predictions. Extensive experiments conducted on the nuScenes dataset confirm the superior performance of the PMM-MOT framework compared to other state-of-the-art trackers, achieving an Average Multi-Object Tracking Accuracy (AMOTA) of **78.4**.

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
