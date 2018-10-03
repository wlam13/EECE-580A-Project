# EECE-580A-Project

Project for EECE-580A for Cyber Physical Security Systems.

This project is an in depth review based on the paper Side-Channel Inference Attacks on Mobile Keypads Using Smartwatches by Anindya Maiti, Murtuza Jadliwala, Jibo He, and Igor Bilogrevic. The paper covers side-channel attacks vulnerabilities on smart phones. Specifically the side channel attacks used are keystroke inference attacks on smartphone touchpads with a smart watch motion sensor. 

Personal Notes and Summary - 

Sensors - accelerometer and gyroscope (in smartwatch) can be used to identify the tapped keystroke. 
Only 3 typing scenarios considered:
(a) Same Hand and Non-Holding Hand Typing (SH-NHHT) 28.44%
(b) Same Hand and Holding Hand Typing (SH-HHT) -- 32.83%
(c) Different Hand and Non-Holding Hand Typing (DHNHHT)-- 2.11%

(d) numeric keypad used in our experiments -- Remaining % -- 36.62%

Smartwatch -> Smartphone -> App logs accelerometer measurements (from wrist motion pattern)
  - Time stamped readings of smartwatch's linear accelerometer (A)
  - Timestamped key press labels (L)
  
  From these readings, algorithm is used to detect keystroke pressed:
  From the paper
_________________________________________________________________________
Algorithm 1. Key Press Detection Algorithm
function KEYPRESS_DETECTION(ATarget)
KeyPresses = f;g
Threshold = Set ThresholdðÞ
for i ¼ 1 to N (N samples in A) do
if Energy[i] >= Threshold then
ThisKeyPress = A[i - 3] to A[i + 15]
Insert ThisKeyPress into KeyPresses
i = i þ 15
end if
end for
end function
_________________________________________________________________________

5 Different Classification Features (for identifying keystroke given data)
1. Simple Linear Regrression (SLR)
2. Random Forst (RF)
3. K-Nearest Neighbors (k-NN)
4. Support Vector Machine (SVM)
5. Bagged Descision Trees (BDT)

Ensamble Classification Approach - Majority vote out of the 5 classications determines result, not just 1 classifcation alone

