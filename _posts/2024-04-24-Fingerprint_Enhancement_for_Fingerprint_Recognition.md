# **Fingerprint Enhancement for Fingerprint Recognition**  

## **Why fingerprint enhancement?**          
Because there may be some additional interference during fingerprint acquisition, this may cause the acquired image to be affected in the following ways.
> A. The ridge lines of the fingerprints are not perfectly connected, resulting in interruptions in the middle.          
> B. Some fingerprints are damaged, resulting in loss of information during fingerprint acquisition.       
> C. The brightness of some fingerprints is not high enough during fingerprint acquisition, resulting in too many dense ridge lines.            

![Original fingerprint image](/master/images//master/images/Confusion_matrix.jpg "Original fingerprint image")           

In this case, it is difficult to extract the features of fingerprints in fingerprint recognition, so it is necessary to enhance the fingerprint image.            

### **Methods of Fingerprint Enhancement**
The most widely accepted image enhancement technique is context filtering in the spatial and frequency domains, which reduces the effects of broken ridges and unwanted scars on fingerprints.      
The specific steps are shown below:
1. **Normalization**: Adjusts the gray values of the image so that the image has a preset mean and variance, which reduces the variation in gray values between ridges and valleys in preparation for subsequent processing steps.              
![Normalization fingerporint](/master/images//master/images/Normalization_fingerporint.jpg "Normalization fingerporint")

2. **Local Orientation Estimation**: this step estimates the ridge direction for each image block. The algorithm divides the image into blocks of size w x w. Then for each block the gradient operator is used to compute its gradient and the ridge direction is estimated by the least squares approach
3. **Local frequency estimation**: After estimating the ridge direction, the algorithm calculates the ridge frequency for each block, i.e., the repetition interval of the ridge and valley structures. The frequency estimation depends on the ridge direction and utilizes the properties of a sinusoidal waveform to model the ridge and valley structures.        
![Predict direction fingerprint](/master/images//master/images/Predict_direction_fingerprint.jpg "Predict direction fingerprint")          

4. **Area mask estimation**: determines which areas of the image are recoverable and which are not by evaluating the ridge and valley characteristics of each block.   
5. **Filtering**: Filtering the image  by applying a set of Gabor filters tuned to the direction and frequency of the local ridges effectively removes noise and preserves the true ridge and valley structure.              
![Gabor filter](/master/images//master/images/Gabor_filter.jpg "Gabor filter")

## **Fingerprint Enhanced Results**
Fingerprints before enhancement:
![Original fingerprint image](/master/images//master/images/Confusion_matrix.jpg "Original fingerprint image")           

Fingerprints after enhancement:
![Enhanced fingerprint image](/master/images//master/images/Enhanced_fingerprint_image.jpg "Enhanced fingerprint image")          

It can be seen that the fingerprint image enhancement algorithm can effectively improve the quality of the input image, especially the clarity of the fingerprint ridges and valleys, thus improving the accuracy and reliability of the automatic fingerprint identification system.
