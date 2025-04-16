# THE Personal Understanding for MCC(Minutia cylinder Code) method 

> Date: April 16, 2025
---
> ## Motivation for MCC method ？

For fingerprint recognition algorithm, it can be seen from the content of courseware, It can be divided into global minutiae based approach and local minutiae based approach. the principle of the global based approach is applya global transformation thatallows to maximize the number of resulting paired minutiae. However, the problem is that it ignores the local information and is sensitive to the transformation of fingerprint images, so the robustness is not strong.

**The principle of the global minutiae-based method is shown below:**     
![global method](/images/global method.png "global minutiae-based method")    
Figure 1: Confusion Matrix (image credit: <https://blog.csdn.net/seagal890/article/details/105059498>)       

Therefore, the local minutiae-based approach is generally adopted, such as Nearest-neighbor-based local structures and Fixed-radius-based local structures. However, the disadvantages of nearest-neighbor-based local structures include the possibility of exchanging nearest neighbor minutiae due to missing or missing false minutiae.  

                                                         
The parameters in the image are respectively:                           
> - **True Positive (TP):** The true class of the sample is positive, and the result of the model identification is also positive.                  
> - **False Negative (FN):** The true class of the sample is positive, but the model recognizes it as negative.                   
> - **False Positive (FP):** The true class of the sample is negative, but the model recognizes it as positive.                  
> - **True Negative (TN):** The true class of the sample is negative, and the model recognizes it as a negative class.      
---
