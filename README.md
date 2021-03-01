# ridgeness_for_lane_detection
This is useful technique with the aim of having a more reliable lane marking detection under adverse circumstances
## **Table of Contents**
- [Mathematics Model](#mathematics-model)
- [Results](#results)

The ridges is defined as longitudinal center of the lane marker as depicted is figure belows [1]  

![ridge.png](/image/ridge.png?raw=true)  

The left side in the above figure depicts a road image with a ROI outlined and also shows what we call center lines of the road lane. The right side of this image shows a landscape of mentioned ROI. The lane lines resemble mountains and their ridges correspond to the center lines of it. 

## **Mathematics Model**
The authors in [1] proposed a mathematics definition to modelize ridges.  
Let <img src="https://render.githubusercontent.com/render/math?math=L\big(x\big)"> be the grey-level image and <img src="https://render.githubusercontent.com/render/math?math=G_{\sigma}\big(x\big)"> be a 2D gaussian filter of standard deviation <img src="https://render.githubusercontent.com/render/math?math=\sigma">, then, smoothed verson of the image is defined as: <img src="https://render.githubusercontent.com/render/math?math=L_{\sigma}\big(x\big)=G_{\sigma}\big(x\big)*L\big(x\big)">, in which, * denotes convolutional multiple.  
Gradient vector field of image can be determined as: <img src="https://render.githubusercontent.com/render/math?math=w_{\sigma}\big(x\big)=\big(\partial_{u}L_{\sigma}\big(x\big),\partial_{v}L_{\sigma}\big(x\big)\big)^T">, in which, u is a column and v is a row of image.  
Structure tensor field of image can be computed as: <img src="https://render.githubusercontent.com/render/math?math=S_{\sigma}\big(x\big)=G_{\sigma}\big(x\big)w_{\sigma}\big(x\big)w_{\sigma}^T\big(x\big)">  
Obtain the eigenvector corresponding to the highest eigenvalue of <img src="https://render.githubusercontent.com/render/math?math=S_{\sigma}\big(x\big)">, namely <img src="https://render.githubusercontent.com/render/math?math=v_{\sigma}\big(x\big)">. It is known that <img src="https://render.githubusercontent.com/render/math?math=v_{\sigma}\big(x\big)"> yields the dominant gradient orientation of the original image at pixel x and is perpendicular to the dominant image orientation at pixel x.  
In the next step, we need to adjust orientation of <img src="https://render.githubusercontent.com/render/math?math=v_{\sigma}\big(x\big)"> according to orientation of gradient itself <img src="https://render.githubusercontent.com/render/math?math=w_{\sigma}\big(x\big)"> by projecting <img src="https://render.githubusercontent.com/render/math?math=v_{\sigma}\big(x\big)"> to <img src="https://render.githubusercontent.com/render/math?math=w_{\sigma}\big(x\big)"> as: <img src="https://render.githubusercontent.com/render/math?math=p\big(x\big)=v_{\sigma}^T\big(x\big)w_{\sigma}\big(x\big)"> and defining the following vector field: <img src="https://render.githubusercontent.com/render/math?math=\tilde{w}\big(x\big)=sign\big(p\big(x\big)\big)v_{\sigma}\big(x\big)">  
Last but not least, our ridgeness measure is defined as the positive values of <img src="https://render.githubusercontent.com/render/math?math=\tilde{\kappa}\big(x\big)=-div\big(\tilde{w}\big(x\big)\big)">, in which <img src="https://render.githubusercontent.com/render/math?math=div\big(\big)"> means divergence of a vector field and the positive values of <img src="https://render.githubusercontent.com/render/math?math=\tilde{\kappa}\big(x\big)"> give a degree of how much an image pixel resembles a ridge point.  
## **Results**

## **Reference**
- [1] A. Lopez et.al, 2005, "Detection of lane markings based on ridgeness and RANSAC", Proceedings of IEEE Intelligent Transportation Systems, http://www.cvc.uab.es/adas/publications/lopez_itsc2005.pdf