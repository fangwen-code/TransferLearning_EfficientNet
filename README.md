一、复现文献：Lung-EffNet: Lung cancer classification using EfficientNet from CT-scan images

二、训练过程：
1) 训练集数据增强：
https://www.kaggle.com/code/fangwenkaggle/5fold-transferlearning-lungcancer-aug
2) 训练集未进行数据增强：
https://www.kaggle.com/code/fangwenkaggle/5fold-transferlearning-lungcancer-no-aug
3) 数据增强前后性能对比：
<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/cb326fe7-fe79-4c80-b338-af3dc3f68c73" />

注：相关结果及代码详见上述训练过程链接即可获得。

三、最佳模型相关结果：

<img width="400" height="300" alt="efficientnet-b1 aug 3-fold epoch Loss plot" src="https://github.com/user-attachments/assets/8a8af750-f021-4dff-b708-027d2e7c797c" />
<img width="400" height="300" alt="efficientnet-b1 aug 3-fold epoch Acc plot" src="https://github.com/user-attachments/assets/b42567a7-6b8c-43d4-a32a-dd6eecdfa520" />

<img width="400" height="300" alt="efficientnet-b1 aug 3-fold test ROC" src="https://github.com/user-attachments/assets/d36d2fe6-3833-4ec1-8ed2-5bd400dfab2a" />
<img width="400" height="300" alt="efficientnet-b1 aug 3-fold test confusion_matrix" src="https://github.com/user-attachments/assets/efb8a4d2-c711-4b59-bda8-a2eeb79b0067" />


