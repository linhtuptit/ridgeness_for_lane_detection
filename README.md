# ridgeness_for_lane_detection
This is useful technique with the aim of having a more reliable lane marking detection under adverse circumstances
## **Table of Contents**
- [Mathematics Model](#mathematics-model)
- [Results](#results)

## **Mathematics Model**
The authors in [1] proposed a mathematics definition to modelize ridges. Let <img src="https://render.githubusercontent.com/render/math?math=L\big(x\big)"> be the grey-level image and <img src="https://render.githubusercontent.com/render/math?math=G_{\sigma}\big(x\big)"> be a 2D gaussian filter of standard deviation <img src="https://render.githubusercontent.com/render/math?math=\sigma">, then, smoothed verson of the image is defined as: <img src="https://render.githubusercontent.com/render/math?math=L_{\sigma}\big(x\big)=G_{\sigma}\big(x\big)*L\big(x\big)">, in which, * denotes convolutional multiple.  
Gradient vector field of image can be determined as: <img src="https://render.githubusercontent.com/render/math?math=w_{\sigma}\big(x\big)=\big(\partial_{u}L_{\sigma}\big(x\big),\partial_{v}L_{\sigma}\big(x\big)\big)^T">, in which, u is a column and v is a row of image.  
Structure tensor field of image can be computed as: <img src="https://render.githubusercontent.com/render/math?math=S_{\sigma}\big(x\big)=G_{\sigma}\big(x\big)w_{\sigma}\big(x\big)w_{\sigma}^T\big(x\big)">    


## **Results**

## **Reference**
- [1] A. Lopez et.al, 2005, "Detection of lane markings based on ridgeness and RANSAC", Proceedings of IEEE Intelligent Transportation Systems, http://www.cvc.uab.es/adas/publications/lopez_itsc2005.pdf