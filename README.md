# TIoU-metric
Release on 27/03/2019. This repository is built on the ICDAR 2015 evaluation code.

# Description
Evaluation protocols plays key role in the developmental progress of text detection methods. There are strict requirements to ensure that the evaluation methods are fair, objective and reasonable. However, existing metrics exhibit some obvious drawbacks: 

<div align=center><img src="Readme_sources/1.png" width="80%" ></div>
*Unreasonable cases obtained using recent evaluation metrics. (a), (b), (c), and (d) all have the same IoU of 0.66 against the GT. Red: GT. Blue: detection.

* As shown in (a), previous metrics consider that the GT has been entirely recalled.

* As shown in (b), (c), and (d), even if containing background noise, previous metrics consider such detection to have 100% precision.

* Previous metrics consider detections (a), (b), (c), and (d) to be equivalent perfect detections. 

* Previous metrics severely rely on an IoU threshold. High IoU threshold may discard some satisfactory bounding boxes, while low IoU threshold may include several inexact bounding boxes.

To address many existing issues of previous evaluation metrics, we propose an improved evaluation protocol called **Tightnessaware Intersect-over-Union (TIoU) metric** that could quantify:

* **Completeness of ground truth**

* **Compactness of detection**

* **Tightness of matching degree**

We hope this work can raise the attentions of the text detection evaluation metrics and serve as a modest spur to more valuable contributions. More details can be found on our [paper](https://arxiv.org/abs/1904.00813). 

# Clone the TIoU repository
Clone the TIoU-metric repository
  ```Shell
  git clone https://github.com/Yuliang-Liu/TIoU-metric.git --recursive
  ```

# Getting Started
Install required module
  ```Shell
  pip install Polygon2
  ```
Then run
  ```Shell
  python script.py -g=gt.zip -s=pixellinkch4.zip
  ```
After that you can see the evaluation resutls.

 You can simply replace pixellinkch4.zip with your own dection results, and make sure your dection format follows the same as [ICDAR 2015](http://rrc.cvc.uab.es/?ch=4&com=tasks).

# Joint Word&Text-Line Evaluation
  To test your detection with our joint Word&Text-Line solution, simply
  ```Shell
  cd Word_Text-Line
  ```
  Then run the code
  ```Shell
  python script.py -g=gt.zip -gl=gt_textline.zip -s=pixellinkch4.zip
  ```
# Support Curved Text Evaluation
  Curved text requires polygonal input with mutable number of points. To evaluate your results on recent curved text benchmarks [Total-text](https://github.com/cs-chan/Total-Text-Dataset) or [SCUT-CTW1500](https://github.com/Yuliang-Liu/Curve-Text-Detector), you can refer to curved-tiou/readme.md.
   
# Example Results
### Qualitative results:
<div align=center><img src="Readme_sources/1-2.png" width="100%" ></div>
*Qualitative visualization of TIoU metric. Blue: Detection. Bold red: Target GT region. Light red: Other GT regions. Rec.: Recognition results by CRNN [24]. NED: Normalized edit distance. Previous metrics evaluate all detection results and target GTs as 100% precision and recall, respectively, while in TIoU metric, all matching pairs are penalized by different degrees. Ct is defined in Eq. 10. Ot is defined in Eq. 13. Please refer to our paper for all the references. <br/>
  
### ICDAR 2013 results:
<div align=center><img src="Readme_sources/1-3.png" width="100%" ></div>
*Comparison of evaluation methods on ICDAR 2013 for general detection frameworks and previous state-of-the-art methods. det: DetEval. i: IoU. e1: End-to-end recognition results by using CRNN [24]. e2: End-to-end recognition results by using RARE [25]. t: TIoU. <br/>
  
### Line chart:
<div align=center><img src="Readme_sources/1-5.png" width="80%" ></div>
*(a) X-axis represents the detection methods listed in the Table above, and Y-axis represents the values of the F-measures.  <br/>
  
### ICDAR 2015 results:
<div align=center><img src="Readme_sources/1-4.png" width="100%" ></div>
*Comparison of metrics on the ICDAR 2015 challenge 4. Word&Text-Line Annotations use our new solution to address OM and MO issues. i: IoU. s: SIoU. t: TIoU. <br/>

## Citation
If you find our metric useful for your reserach, please cite (comming soon)

## References
If you are insterested in developing better scene text detection metrics, some references recommended here might be useful.

[[1]](https://link.springer.com/article/10.1007/s10032-006-0014-0) Wolf, Christian, and Jean-Michel Jolion. "Object count/area graphs for the evaluation of object detection and segmentation algorithms." International Journal of Document Analysis and Recognition (IJDAR) 8.4 (2006): 280-296.

[[2]](https://www.sciencedirect.com/science/article/pii/S0262885615001377) Calarasanu, Stefania, Jonathan Fabrizio, and Severine Dubuisson. "What is a good evaluation protocol for text localization systems? Concerns, arguments, comparisons and solutions." Image and Vision Computing 46 (2016): 1-17.

[[3]](https://ieeexplore.ieee.org/abstract/document/8395220) Dangla, Aliona, et al. "A first step toward a fair comparison of evaluation protocols for text detection algorithms." 2018 13th IAPR International Workshop on Document Analysis Systems (DAS). IEEE, 2018.

[[4]](https://ieeexplore.ieee.org/abstract/document/8270164) Shi, Baoguang, et al. "ICDAR2017 competition on reading chinese text in the wild (RCTW-17)." 2017 14th IAPR International Conference on Document Analysis and Recognition (ICDAR). Vol. 1. IEEE, 2017.

## Feedback 
  Suggestions and opinions of this metric (both positive and negative) are greatly welcome. Please contact the authors by sending email to 
  `liu.yuliang@mail.scut.edu.cn` or `yuliang.liu@adelaide.edu.au`.

 <meta http-equiv="refresh" content="2.5">

