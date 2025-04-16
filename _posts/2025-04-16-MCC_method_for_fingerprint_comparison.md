# THE Personal Understanding for MCC(Minutia cylinder Code) method 

> Date: April 16, 2025
---
> ## Motivation for MCC method ？

For fingerprint recognition algorithm, it can be seen from the content of courseware, It can be divided into global minutiae based approach and local minutiae based approach. the principle of the global based approach is **applya global transformation thatallows to maximize the number of resulting paired minutiae.** However, the problem is that it ignores the local information and is sensitive to the transformation of fingerprint images, so the robustness is not strong.

The principle of the global minutiae-based method is shown below:    
<div align="center"> <img src="/images/global method.png" width = 600 height = 300 /> </div>
<div align="center"> Figure 1: global minutiae-based method  </div>

Therefore, the local minutiae-based approach is generally adopted, such as Nearest-neighbor-based local structures and Fixed-radius-based local structures. For Nearest-neighbor-based local structures, the schematic diagram is as follows:

 ![这是图片](/images/K-near.jpeg "Magic Gardens")
 
Its disadvantages are:
- possibility of exchanging nearest neighbor minutiae due to missing or false minutiae.

For Fixed-radius-based local structures, the schematic diagram is as follows:

 ![这是图片](/images/R-nei.jpeg "Magic Gardens")
 
Its disadvantages include:
- the descriptor length is variable and depends on the local
 minutiae density leading to a more complex comparison.
- minutiae close to the border can be mismatched because
 of different local distortion or location inaccuracy.

Therefore, the method of Minutiae cylinder code is introduced in the courseware. Its advantages are as follows:
- fixed radius structure;
- fixed-length descriptors;
- tolerates local distortion and small feature extraction errors;
- bit-oriented coding;
- fast and simple local structure comparison phase;

[参考课件链接](https://markdown.com.cn)。

Therefore, the MCC method is currently used for fingerprint recognition.

 ---
## the general algorithm process for MCC method
The process of understanding MCC fingerprint matching method from courseware can be abstracted as the following steps

| step | step description | 
|------|------------------| 
| step1 | A discrete cylinder is constructed by selecting the radius and quantizing the transverse and longitudinal values |
| step2 | The values on the cylinder are calculated according to the spatial location of other minutiae in the radius domain |
| step3 | The values in each layer of the cylinder are determined according to the directional difference and Gaussian distribution between other minutiae in the radius field and the current minutiae |
| step4 | Convert cylinders into bit vectors based on the unit step function|
| step5 | Performing fractions on two cylinders|

These steps are just a personal abstract understanding, and the formula for calculating the specific score regarding step 5 is as follows:

$$
\gamma(a,b) = 1 - \frac{\|C_a \oplus C_b\|}{\|C_a\| + \|C_b\|}
$$

## conclusion
Based on the MCC method, the local features of fingerprints can be better extracted, including the spatial location and orientation information of other minutiae within its radius R, so as to better match the features, and tolarate the aberration of the image and the overall transformation, which is more robust.
     
---
