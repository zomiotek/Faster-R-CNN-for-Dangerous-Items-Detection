# Faster R-CNN for Dangerous Items Detection (PyTorch implementation)

There are many implementations of Faster R-CNNs available in the Internet. Unfortunately, most of them contain bugs or were designed for older versions of Python and machine learning libraries. After testing many such solutions, I used one of the few implementations designed for newer versions of PyTorch and TensorFlow. This implementation was shared by Bart Trzynadlowski on the https://github.com/trzy/FasterRCNN website. After removing a number of bugs and making the necessary changes to the configuration of the training and evaluation processes, I applied an implementation for PyTorch to build the Faster R-CNN model for dangerous items detection. The _packages.txt_ file contains the necessary libraries and their versions. The dataset I used can be downloaded from the Zenodo platform: https://zenodo.org/records/11582054. Sample images belonging to different categories are shown below.

![image](https://github.com/user-attachments/assets/7df790c5-1f31-4207-a931-c7d3035c277d)

You can use different kind of backbones to build the Faster R-CNN model but my experiments showed that the ResNet152 provides higher accuracy compared to other architectures (https://www.preprints.org/manuscript/202406.1090/v1). The entire learning process consists of 2 stages. In the first one, the learning speed is 1E-3, while in the second stage, the value is 1E-4. After each training epoch, the mean average precision (mAP) of the model is calculated based on the test set. At the same time, the weights obtained in a given era are saved, so that you can choose the best set of weights after the entire training process is completed.

In order to conduct training and evaluation, 3 batch files were prepared:

_train.bat_ – starts the 1st stage of training with a learning speed of 1E-3;

_tune.bat_ – starts the 2nd stage of training with a learning speed of 1E-4;

_eval.bat_ – performs an evaluation for the test set and calculates a set of parameters to assess the quality of the model.

The _tune.bat_ and _eval.bat_ files use the NUMBER variable, which stores the number of the model with the best weights built during the previous stage. The information about the best models is displayed after the 1st and 2nd stages of training. For more information on implementation details, visit https://github.com/trzy/FasterRCNN.

Selected excerpts from an experiment in which the above implementation of Faster R-CNN was used are shown in this video: https://zenodo.org/records/12736924.
