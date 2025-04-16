# THE Personal Understanding for MCC(Minutia cylinder Code) method 

> Date: April 16, 2025
---
> ## Motivation for MCC method ？

For fingerprint recognition algorithm, it can be seen from the content of courseware, It can be divided into global minutiae based approach and local minutiae based approach. the principle of the global based approach is **applya global transformation thatallows to maximize the number of resulting paired minutiae.** However, the problem is that it ignores the local information and is sensitive to the transformation of fingerprint images, so the robustness is not strong.

The principle of the global minutiae-based method is shown below:    
<div align="center"> <img src="/images/global method.png" width = 600 height = 300 /> </div>
<div align="center"> Figure 1: global minutiae-based method  </div>

Therefore, the local minutiae-based approach is generally adopted, such as Nearest-neighbor-based local structures and Fixed-radius-based local structures. For Nearest-neighbor-based local structures, the schematic diagram is as follows:

<div align="center"> <img src="/images/k closest.png" width = 300 height = 300 /> </div>
<div align="center"> Figure 2: The principle of the k Nearest neighbor based local structures </div>
 
Its disadvantages are:
- possibility of exchanging nearest neighbor minutiae due to missing or false minutiae.

For Fixed-radius-based local structures, the schematic diagram is as follows:

<div align="center"> <img src="/images/R neih.png" width = 300 height = 300 /> </div>
<div align="center"> Figure 3: The principle of the Fixed radius based local structures </div>
 
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

[Reference](https://learn-ap-southeast-2-prod-fleet01-xythos.content.blackboardcdn.com/5fd17f67f4120/35036162?X-Blackboard-S3-Bucket=learn-ap-southeast-2-prod-fleet01-xythos&X-Blackboard-Expiration=1744826400000&X-Blackboard-Signature=xuTuFcrFu6LZvtqqrXWfkrVQm6Q1Hq8HkPeRwpvbabA%3D&X-Blackboard-Client-Id=149017&X-Blackboard-S3-Region=ap-southeast-2&response-cache-control=private%2C%20max-age%3D21600&response-content-disposition=inline%3B%20filename%2A%3DUTF-8%27%27Lecture6.pdf&response-content-type=application%2Fpdf&X-Amz-Security-Token=IQoJb3JpZ2luX2VjELz%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0yIkcwRQIgehIhU8BvPkaBis4SVrS5GcFAJiFp%2FXPOBX9er4JHi8wCIQCXKWNM9zJQzjlGG0%2F3KpnwIi50kLv4a0DIemH9%2Bjv7cirCBQhFEAAaDDU1NjkwMzg2MTM2MSIMF0q7mHB0o5s%2BkcCvKp8FB0chF49MHe9JGgD5fdg3OnoThsEsAg3%2Ff%2BsIk2vss70rlYMX5Jom%2BzYL4OwkC7%2FvZHjh1qHKq0tGCvJ8xr%2F0zW%2BIrCQwnnH7%2B3ymYhbq4xOObhrs81YY4ZCuZx8nww7GUYKTSsOxhrVMRiv6C5rygVFPA3zCYBhQJEA3%2BB%2BZF9bVssi1FurY7L7NZbYMk7Zpb0h%2FYnOu0dukJzlRVNaX3XN6c2DMEm3acBCXBjdCEydySA%2FrUh%2BuZ3ahA23SE4pJSrPyWB6z3ui9Tr632JTvaVKkA%2Fp3bomj3%2FJYs9IvKq0WaZ85nHhMsyTtuK0Neup6%2FtdwQAI%2BrSCU9Zv5VRbRPZHwzGfONfFVPekUI7XlzQNm%2FUG7igDo9uGpXZ2V9g7L1myXG9w9wqSok7cn%2Foo84QSI0Q9ZLC2XBCFBYY2vLRmtEm4TdByaEWAumX2jjQGTfJbhe%2BNHiX8GLYFPZ%2F2I7wG6X%2FmpTgmhSJuKJlufLjdX3zqf4Cm4Kf5MmP6JmcXzDd8Zr%2FiZo3wa01yToJJ7cL2cpTfmGyD%2FAMaKul1rtS9sUuuYGPYY%2B%2Fa8e4AemFlRfHnHCUI1fPEasJRD8la66rs5%2Bn3SKsvgCpm0fSmNvy0xhiDJNjCCOLinQEBfsG0L23nrmwz0nDTbDd1hF2aCE3DEvLoNuSqpa4cyA%2BB0KzhlwrqSG0KBDJpr46P0kQvBgVOjdTbV0FsyyvXCdXfTbYGSVP9SuL5XtruSxOJ5zwuOAfomXvw%2Bed9AdukzZ%2FRXrZOLZJYsJocpEViiuk%2FKOn2Sf%2BXbK6axRfudTT%2F8PnXuhfqE3sqEbP5RbqNXve66K1U3Zzl1UKVlyKFl08pVs7071WwiaojwZZQfhJfvSZW1F%2FCYpH2EumfEdRLZSDQw2sH%2BvwY6sQFbC%2FMCQJ9ovOwOC3L1U22Lnn93FVS0VVbWxuuSDUEUWuT3FxT6%2FFzqKnG1XyXkx7jQmdmiCOvO2PkOVhUkEex2V84hWGuSGBmW7UmpvHPlTqD9odz5H%2BxzINim6xuFXtYtbMTpd%2FR%2FqeDpdK%2BS%2BRkVxnF9ZCtNMvXTftLpn6xbEE4FBnT%2BKW4hND1fHlGKvP5W1oDynlYs6imxeBOxs3gAR56QPg4aTww8JVQ0Nwwvxhs%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20250416T120000Z&X-Amz-SignedHeaders=host&X-Amz-Expires=21600&X-Amz-Credential=ASIAYDKQORRYUXR4HV6P%2F20250416%2Fap-southeast-2%2Fs3%2Faws4_request&X-Amz-Signature=eae036b46c204737338b405cee2ff21e69a4f4906aa2741dcaad247eaa472071)

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

---

## conclusion
Based on the MCC method, the local features of fingerprints can be better extracted, including the spatial location and orientation information of other minutiae within its radius R, so as to better match the features, and tolarate the aberration of the image and the overall transformation, which is more robust.
     
---
