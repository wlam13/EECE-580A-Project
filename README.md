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

How Classifiers Were Tested:

Participants input numbers based on random number audio stream

Before Combining Smartwatch and Smartphone Data:
One versus One: From same individual participant- 84.58% accuracy for SH-NHHT, 83.5% accuracy for SH-HHT, <12min computation time
One versus Rest: From one participant against rest of participants- 70.08% accuracy for SH-NHHT and 85.83% accuracy for SH-HHT, <21min computation time
All versus All: Percentage of correct inferences on all participants against classifiers trained from training set of all participants
- accuracy of 88.16% for SH-NHHT and 85.83% for SH-HHT, 34min computation time

Lower Accuracy with lower sampling frequency but still fairly accurate (see figure 7 in paper)

Accuracy increased marginally after Smartwatch and Smartphone data were used in combination

When typing at a more natural speed (faster): 
Classification accuracy dropped. Mean Classification accuracy of 52% for SH-NHHT and 61% for SH-HHT

Cross Device Performance: 
Classification accuracy lowered in large variations, some by a few percentage points and some dropping over 30 percentage points

QWERTY Keypads:
Classifciation accuracy lowered to below 50% in all alphabet cases, may be possible to improve accuracy by analyzing keyboard characteristics or by performing dictionary based search




