# EIP_Session5

Thanks for this wonderful assignment. Honestly, I was too busy and could not do justice to this assignment. But following are the things I tried:

1. I understood to great extent how to implement subclassed models. However I did not go beyond Davidnet. But tries to implement Cyclic LR, Data sugmentation, and different gradient calculations for different outputs. 
2. I saw some errors in data. For example people with back pose had emotion other than neutral. So I made that all Neutral. Also I saw that some classes were heavily skewed, so I added some more examples via augmentation of other classes.
3. I tried all ways sequestial (theough someone else as I didnt have time to do it myself), functigonal and subclassing. Larger models were giving OOM error and thus have to revert to smaller networks or deeper with separable conv only.

First try after 11 epochs [link](https://github.com/abhinavdayal/EIP_Session5/blob/master/Davidnet_PersonAttributes_success01.ipynb):

```
EPOCH:11, lr: 0.001, train loss: 0.79, train acc: 0.67, val loss: 0.81, val acc: 0.63, time: 0:02:03.843247
GENDER_OUTPUT: [TRAIN] loss: 0.34, acc: 0.85, [TEST] loss: 0.36, acc: 0.82
IMAGEQUALITY_OUTPUT: [TRAIN] loss: 0.87, acc: 0.58, [TEST] loss: 0.91, acc: 0.55
AGE_OUTPUT: [TRAIN] loss: 1.32, acc: 0.42, [TEST] loss: 1.31, acc: 0.35
WEIGHT_OUTPUT: [TRAIN] loss: 0.93, acc: 0.64, [TEST] loss: 0.92, acc: 0.63
CARRYINGBAG_OUTPUT: [TRAIN] loss: 0.80, acc: 0.65, [TEST] loss: 0.91, acc: 0.58
FOOTWEAR_OUTPUT: [TRAIN] loss: 0.73, acc: 0.68, [TEST] loss: 0.75, acc: 0.66
EMOTION_OUTPUT: [TRAIN] loss: 0.86, acc: 0.71, [TEST] loss: 0.89, acc: 0.68
BODYPOSE_OUTPUT: [TRAIN] loss: 0.47, acc: 0.81, [TEST] loss: 0.46, acc: 0.80
```

Second try with CLR: [link](https://github.com/abhinavdayal/EIP_Session5/blob/master/Experiment_05_Davidnet_PersonAttributes_CLR_multigrad%2C_multilr.ipynb). Here I did data augmentation trying to remove skweness in distribution. Dont look at test_acc, it is dividing by original length of train data rather than the new augmented length. 
```
GENDER_OUTPUT: [TRAIN] loss: 2.02, acc: 5.30, [TEST] loss: 0.39, acc: 0.81
IMAGEQUALITY_OUTPUT: [TRAIN] loss: 5.56, acc: 3.52, [TEST] loss: 0.92, acc: 0.53
AGE_OUTPUT: [TRAIN] loss: 8.80, acc: 2.30, [TEST] loss: 1.53, acc: 0.31
WEIGHT_OUTPUT: [TRAIN] loss: 7.08, acc: 3.17, [TEST] loss: 1.14, acc: 0.50
CARRYINGBAG_OUTPUT: [TRAIN] loss: 5.76, acc: 3.49, [TEST] loss: 0.91, acc: 0.56
FOOTWEAR_OUTPUT: [TRAIN] loss: 4.70, acc: 4.12, [TEST] loss: 0.82, acc: 0.60
EMOTION_OUTPUT: [TRAIN] loss: 6.97, acc: 3.04, [TEST] loss: 1.19, acc: 0.37
BODYPOSE_OUTPUT: [TRAIN] loss: 2.85, acc: 5.05, [TEST] loss: 0.56, acc: 0.75
```

Third try without CLR but same as above: [link]()
