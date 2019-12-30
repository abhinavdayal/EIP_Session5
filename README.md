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

Second try with CLR: [link](https://github.com/abhinavdayal/EIP_Session5/blob/master/Experiment_05_Davidnet_PersonAttributes_CLR_multigrad%2C_multilr.ipynb). 

Here I did data augmentation trying to remove skweness in distribution. Dont look at test_acc, it is dividing by original length of train data rather than the new augmented length. 
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

Third try without CLR but same as above: [link](https://github.com/abhinavdayal/EIP_Session5/blob/master/Experiment_05_Davidnet_PersonAttributes_multigrad%2C_multilr.ipynb)
```
EPOCH:6, global_step = 13398, lr: 0.001, train loss: 0.28, train acc: 0.90, val loss: 1.21, val acc: 0.58, time: 1:39:22
GENDER_OUTPUT: [TRAIN] loss: 0.10, acc: 0.96, [TEST] loss: 0.47, acc: 0.83
IMAGEQUALITY_OUTPUT: [TRAIN] loss: 0.34, acc: 0.87, [TEST] loss: 1.36, acc: 0.49
AGE_OUTPUT: [TRAIN] loss: 0.46, acc: 0.83, [TEST] loss: 2.06, acc: 0.35
WEIGHT_OUTPUT: [TRAIN] loss: 0.32, acc: 0.88, [TEST] loss: 1.45, acc: 0.49
CARRYINGBAG_OUTPUT: [TRAIN] loss: 0.27, acc: 0.90, [TEST] loss: 1.20, acc: 0.63
FOOTWEAR_OUTPUT: [TRAIN] loss: 0.29, acc: 0.89, [TEST] loss: 1.20, acc: 0.56
EMOTION_OUTPUT: [TRAIN] loss: 0.31, acc: 0.88, [TEST] loss: 1.37, acc: 0.54
BODYPOSE_OUTPUT: [TRAIN] loss: 0.15, acc: 0.95, [TEST] loss: 0.59, acc: 0.79
```

Fourth attempt, tried simple model with separable conv layers [link](https://github.com/abhinavdayal/EIP_Session5/blob/master/Copy_of_simplefunctional_model.ipynb)
```
Epoch 10/10
360/360 [==============================] - 505s 1s/step - loss: 6.8687 - gender_output_loss: 0.4682 - image_quality_output_loss: 0.8920 - age_output_loss: 1.3763 - weight_output_loss: 0.9572 - bag_output_loss: 0.8408 - pose_output_loss: 0.6531 - footwear_output_loss: 0.8160 - emotion_output_loss: 0.8650 - gender_output_accuracy: 0.7784 - image_quality_output_accuracy: 0.5741 - age_output_accuracy: 0.4056 - weight_output_accuracy: 0.6331 - bag_output_accuracy: 0.6216 - pose_output_accuracy: 0.7238 - footwear_output_accuracy: 0.6303 - emotion_output_accuracy: 0.7220 - val_loss: 7.6599 - val_gender_output_loss: 0.4727 - val_image_quality_output_loss: 1.3901 - val_age_output_loss: 1.4065 - val_weight_output_loss: 0.9653 - val_bag_output_loss: 0.9231 - val_pose_output_loss: 0.7189 - val_footwear_output_loss: 0.8854 - val_emotion_output_loss: 0.8979 - val_gender_output_accuracy: 0.7732 - val_image_quality_output_accuracy: 0.3226 - val_age_output_accuracy: 0.3891 - val_weight_output_accuracy: 0.6447 - val_bag_output_accuracy: 0.5393 - val_pose_output_accuracy: 0.6865 - val_footwear_output_accuracy: 0.5872 - val_emotion_output_accuracy: 0.7077
```
fifth attempt, tried resnet v1 20, where first 2 stages are common and last stage is split out. [link](https://github.com/abhinavdayal/EIP_Session5/blob/master/Resnet20.ipynb)
```
Epoch 24/24
360/360 [==============================] - 90s 251ms/step - loss: 5.3916 - gender_output_loss: 0.4668 - image_quality_output_loss: 0.8687 - age_output_loss: 1.3170 - weight_output_loss: 0.9050 - bag_output_loss: 0.8083 - pose_output_loss: 0.5678 - footwear_output_loss: 0.7733 - emotion_output_loss: 0.8203 - gender_output_accuracy: 0.7730 - image_quality_output_accuracy: 0.5852 - age_output_accuracy: 0.4222 - weight_output_accuracy: 0.6478 - bag_output_accuracy: 0.6399 - pose_output_accuracy: 0.7668 - footwear_output_accuracy: 0.6542 - emotion_output_accuracy: 0.7214 - val_loss: 5.7077 - val_gender_output_loss: 0.4852 - val_image_quality_output_loss: 0.9491 - val_age_output_loss: 1.3807 - val_weight_output_loss: 0.9530 - val_bag_output_loss: 0.8420 - val_pose_output_loss: 0.6623 - val_footwear_output_loss: 0.8018 - val_emotion_output_loss: 0.8996 - val_gender_output_accuracy: 0.7631 - val_image_quality_output_accuracy: 0.5640 - val_age_output_accuracy: 0.3886 - val_weight_output_accuracy: 0.6487 - val_bag_output_accuracy: 0.6119 - val_pose_output_accuracy: 0.7238 - val_footwear_output_accuracy: 0.6477 - val_emotion_output_accuracy: 0.7046
```
