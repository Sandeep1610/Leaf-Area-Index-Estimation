# Leaf-Area-Index-Estimation
We used VGG16 architecture as convolutional part to extract image features in Fully Connected Networks.
VGGNet-16 consists of 16 convolutional layers and is very appealing because of its very uniform Architecture. Similar to Alex-Net, it has only 3x3 convolutions, but lots of filters. It is currently the most preferred choice in the community for extracting features from images. The weight configuration of the VGG-Net is publicly available and has been used in many other applications and challenges as a baseline feature extractor.
However, VGG-Net consists of 138 million parameters, which can be a bit challenging to handle. VGG can be achieved through transfer Learning.

Leaf area index calculation:
Once the semantic segmentation result from the network is obtained, LAI can be calculated. The total number of pixels N_Soil  and the number of green leaf pixels N_Leaf are respectively counted. The ratio of the two variables above is the LAI of the image. 
The calculation formula of LAI is as follows   

                                  LAI of the image = N_Leaf/N_Soil  

 Performance evaluation indicators:
Let n_ij be the number of pixels of class i predicted to belong to class j
Let t_i = ∑_i▒〖 n_ij 〗 be the total number of pixels of class i
Pixel accuracy = ∑_i▒〖 n_ii 〗 / ∑_i▒〖 t_i 〗 
IOU: Intersection-Over-Union is a common evaluation metric for semantic image segmentation. The closer the value 1, the higher the overlap between the segmentation result and the label.
                  
The network was trained on dataset which containing 624 plant images. Binary Cross-Entropy Loss is used in our network for iteration and training, before using the loss function above, the sigmoid function must act on the output. Therefore, the value will be between 0 and 1. In our task, since only the leaf part needs to extract, the label should be 0 or 1. 1 is defined as the leaf part and 0 as the background. From the formula above, it is evident that when y_ij is 1, then 1-y_ij is equal to 0. therefore, the closer *y_ij is to 1, and the minor loss will be. The conclusion reaches the same when y_ij is equal to 0. It is in line with our expectations: to make the output close to the label.
