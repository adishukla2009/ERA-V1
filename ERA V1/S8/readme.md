](Session-8 Assignment

      Change the dataset to CIFAR10
      Make this network:
      C1 C2 c3 P1 C3 C4 C5 c6 P2 C7 C8 C9 GAP C10
      Keep the parameter count less than 50000
      Try and add one layer to another
      Max Epochs is 20
      You are making 3 versions of the above code (in each case achieve above 70% accuracy):
      Network with Group Normalization
      Network with Layer Normalization
      Network with Batch Normalization
      Share these details
      Training accuracy for 3 models
      Test accuracy for 3 models
      Find 10 misclassified images for the BN model, and show them as a 5x2 image matrix in 3 separately annotated images.
      write an explanatory README file that explains:
      what is your code all about,
      your findings for normalization techniques,
      add all your graphs
      your collection-of-misclassified-images
      Upload your complete assignment on GitHub and share the link on LMS
      Solution

# The code is in below files

      BN - https://github.com/adishukla2009/ERA-V1/blob/main/ERA%20V1/S8/ERAV1_S8_BN.ipynb
      LN - https://github.com/adishukla2009/ERA-V1/blob/main/ERA%20V1/S8/ERAV1_S8_LN.ipynb
      GN - https://github.com/adishukla2009/ERA-V1/blob/main/ERA%20V1/S8/ERAV1_S8_GN.ipynb

Model Architecture:
    Layer (type)               Output Shape         Param #
================================================================
Conv2d-1 [-1, 32, 32, 32] 864
ReLU-2 [-1, 32, 32, 32] 0
GroupNorm-3 [-1, 32, 32, 32] 64
Dropout-4 [-1, 32, 32, 32] 0
Conv2d-5 [-1, 54, 32, 32] 15,552
ReLU-6 [-1, 54, 32, 32] 0
GroupNorm-7 [-1, 54, 32, 32] 108
Dropout-8 [-1, 54, 32, 32] 0
Conv2d-9 [-1, 10, 32, 32] 540
MaxPool2d-10 [-1, 10, 16, 16] 0
Conv2d-11 [-1, 16, 16, 16] 1,440
ReLU-12 [-1, 16, 16, 16] 0
GroupNorm-13 [-1, 16, 16, 16] 32
Dropout-14 [-1, 16, 16, 16] 0
Conv2d-15 [-1, 16, 16, 16] 2,304
ReLU-16 [-1, 16, 16, 16] 0
GroupNorm-17 [-1, 16, 16, 16] 32
Dropout-18 [-1, 16, 16, 16] 0
Conv2d-19 [-1, 32, 16, 16] 4,608
ReLU-20 [-1, 32, 16, 16] 0
GroupNorm-21 [-1, 32, 16, 16] 64
Dropout-22 [-1, 32, 16, 16] 0
Conv2d-23 [-1, 16, 16, 16] 512
MaxPool2d-24 [-1, 16, 8, 8] 0
Conv2d-25 [-1, 32, 8, 8] 4,608
ReLU-26 [-1, 32, 8, 8] 0
GroupNorm-27 [-1, 32, 8, 8] 64
Dropout-28 [-1, 32, 8, 8] 0
Conv2d-29 [-1, 32, 8, 8] 9,216
ReLU-30 [-1, 32, 8, 8] 0
GroupNorm-31 [-1, 32, 8, 8] 64
Dropout-32 [-1, 32, 8, 8] 0
Conv2d-33 [-1, 32, 8, 8] 9,216
ReLU-34 [-1, 32, 8, 8] 0
GroupNorm-35 [-1, 32, 8, 8] 64
Dropout-36 [-1, 32, 8, 8] 0
AvgPool2d-37 [-1, 32, 1, 1] 0
Conv2d-38 [-1, 10, 1, 1] 320
Total params: 49,672
Trainable params: 49,672
Non-trainable params: 0
Input size (MB): 0.01
Forward/backward pass size (MB): 3.51
Params size (MB): 0.19
Estimated Total Size (MB): 3.71

Accuracy Comparison :(20th Epoch)
BN -79.26
LN - 76.57
GN -76.19

Inference
Batch Normalization is giving best test accuracy. Layer Normalization & Group Normalization test accuracy are also close to Batch Normalization results but on lower side.
BN has relatively smoother graph for Test & Train accuracy than LN and GN

Batch Normalization
Graph 


![image](https://github.com/adishukla2009/ERA-V1/assets/1230195/1a8de3d9-7c96-4457-8046-8be335194ba2)

Misclassified Images 



![image](https://github.com/adishukla2009/ERA-V1/assets/1230195/d6eb4ccf-9753-45d5-96c6-9e80c51b0428)


Layer Norm 
Graph 



![image](https://github.com/adishukla2009/ERA-V1/assets/1230195/81498e5c-98b2-46b2-b709-331dbb35a06e)

Misclassified Images 



![image](https://github.com/adishukla2009/ERA-V1/assets/1230195/110bcbc1-2015-49f2-9722-d911b7d99247)

Group Norm
Graph



![image](https://github.com/adishukla2009/ERA-V1/assets/1230195/c3de3016-9c95-4daf-ac93-68453524392b)

Misclassified Images 



![image](https://github.com/adishukla2009/ERA-V1/assets/1230195/51d31382-3832-4a7f-b725-e8dff29d6015)








