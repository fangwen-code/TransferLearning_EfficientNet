一、介绍  
  该项目参考文献：Lung-EffNet: Lung cancer classification using EfficientNet from CT-scan images  
因该文献未公开代码，故根据文献描述进行复现，文献作者是利用Tensorflow框架，而此处是基于pytorch框架。  

该项目主要包含两个部分：  
1）深度学习模型训练：基于训练集是否进行了数据增强处理的模型训练。   
2）模型基于ONNX Runtime CPU推理性能分析：基于最佳模型开展，包含模型优化，如Conv+BN 融合，模型全量量化/选择性量化。（文献中不涉及此部分，为新增内容）    

二、深度学习模型训练

1、具体代码、训练过程及结果：  

a. 训练集数据增强：  
https://www.kaggle.com/code/fangwenkaggle/5fold-transferlearning-aug-noshape-soft  

b. 训练集未进行数据增强：  
https://www.kaggle.com/code/fangwenkaggle/5fold-transferlearning-noaug-noshape-soft  

c. 数据增强前后性能对比：  
<img width="500" height="400" alt="image" src="https://github.com/user-attachments/assets/f5a400c7-ab42-4494-bcd8-ad32e25b6950" />

2、最佳模型相关结果：  

<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/4fe7e88f-09f2-4bae-81bc-7278f2d0dcf9" />
<img width="400" height="300" alt="image" src="https://github.com/user-attachments/assets/d472ad23-d2bc-4483-92ee-60e519e4f459" />

<img width="400" height="375" alt="image" src="https://github.com/user-attachments/assets/8c2e2dd8-2d3d-480b-9b38-52194cd4e45d" />
<img width="400" height="375" alt="image" src="https://github.com/user-attachments/assets/d55a51e8-0d9c-4fbc-939c-b6ccf7b08624" />  


综上所述：  
a. 基于EfficientNet迁移学习得到的最佳模型实现了整体accuracy近0.95。  
b. 通过训练集数据增强后，各类别的F1-score均有提升，Benign提升最明显，Recall从0.54提升到0.83（AUC从0.95到0.97，保持Malignant高Recall<0.99>的同时）。  

三、ONNX Runtime CPU推理  

1、具体代码、运行过程及结果：  
https://www.kaggle.com/code/fangwenkaggle/transfer-learning-ort-cpu-dynamic-2  

2、相关结果见表格：  
ORT.CPU.inference.xlsx: 该表格sheet1展示了各模型在CPU推理过程中精度的变化情况；sheet2展示了CPU推理过程性能的变化情况；  
从结果来看：Conv+BN 融合为无精度损失优化，而在经过全量量化和选择性量化后，模型压缩率70%+,但精度及性能显著下降。

四、讨论  
1）复现出的结果和文献不一致，可能存在如下原因：  
a. 图像预处理存在差异，如图像肺部切割部分；  
b. 训练集数据增强方式如旋转角度，明暗程度等不同；  
c. 数据集分割差异，虽都是按8：2比例，但可能分出的训练集和测试集不同；  
d. 根据文献workflow，发现验证集和训练集都进行了数据增强，不确定是否为笔误，但本项目是仅针对训练集进行数据增强，并结合5折交叉验证筛选最佳模型。    

2）基于ONNX Runtime CPU推理，发现不符合模型量化后“低延迟，高吞吐”特性。可能存在如下原因：   
a. 模型的关键层（如病灶特征提取层）对量化噪声敏感，导致精度大幅下降; 后续考虑量化感知训练QAT+选择性量化（仅量化非关键层）。  
b. CPU对INT8量化的优化效果不如GPU/TensorRT, 后续考虑利用TensorRT GPU进行推理。  
