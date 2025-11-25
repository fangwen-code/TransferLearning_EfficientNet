一、复现文献：Lung-EffNet: Lung cancer classification using EfficientNet from CT-scan images

二、训练过程：
1) 训练集数据增强：
https://www.kaggle.com/code/fangwenkaggle/5fold-transferlearning-aug-noshape-soft
2) 训练集未进行数据增强：
https://www.kaggle.com/code/fangwenkaggle/5fold-transferlearning-noaug-noshape-soft
3) 数据增强前后性能对比：
<img width="400" height="375" alt="image" src="https://github.com/user-attachments/assets/a63fae73-73c9-4def-9891-5b4be1482983" />

注：相关结果及代码详见上述训练过程链接即可获得。

三、最佳模型相关结果：
<img width="3000" height="1800" alt="efficientnet-b1 aug epoch Loss plot" src="https://github.com/user-attachments/assets/cb9b28cb-602f-43b6-ac0c-4e37832f978f" />
<img width="3000" height="1800" alt="efficientnet-b1 aug epoch Acc plot" src="https://github.com/user-attachments/assets/7ccb6e4a-f438-469e-8f10-f6b3d7abb069" />

<img width="1920" height="1440" alt="efficientnet-b1 aug test ROC" src="https://github.com/user-attachments/assets/07a5b9eb-93af-4fec-b503-79f57acff6b6" />

<img width="2400" height="1800" alt="efficientnet-b1 aug test confusion_matrix" src="https://github.com/user-attachments/assets/9708b2d4-4b28-4d87-98d6-0f0160ac6490" />
