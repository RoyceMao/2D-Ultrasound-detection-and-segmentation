# 2D-Ultrasound-detection-and-segmentation
<br><br>
## 环境
   * Python 3.6.4
   * Keras 2.0.3
   * theano 1.0.3
   * pygpu 0.7.6
   
## 分割效果
<img src="https://github.com/RoyceMao/2D-Ultrasound-detection-and-segmentation/blob/master/img/img_1.png" width="320" height="230"/> <img src="https://github.com/RoyceMao/2D-Ultrasound-detection-and-segmentation/blob/master/img/img_2.png" width="320" height="230"/>
<img src="https://github.com/RoyceMao/2D-Ultrasound-detection-and-segmentation/blob/master/img/img_1_maskpred.png" width="320" height="230"/> <img src="https://github.com/RoyceMao/2D-Ultrasound-detection-and-segmentation/blob/master/img/img_2_maskpred.png" width="320" height="230"/>

## 数据集
   [ultrasound-nerve-segmentation](https://www.kaggle.com/c/ultrasound-nerve-segmentation/data)
   
## KERAS_BACKEND
train_generator.py中添加如下：<br>
```
import os
os.environ['KERAS_BACKEND'] = 'theano'
import keras.backend as K
K.set_image_dim_ordering('th')
```
## KERAS 2.0
data.py、u_net.py、u_model.py均已修改为keras2.0支持，其中u_model的结构相应修改如下：
<img src="https://github.com/RoyceMao/2D-Ultrasound-detection-and-segmentation/blob/master/img/EG.png" width="650" height="250"/>

## numpy数据准备

```
//train文件中，用于train与validation的图片数量之比为4：1，test文件中由于没有对应的掩模标注，只能拿来做预测
python data.py
```

## 训练预测

```
//边训练边加载数据
python train_generator.py
```

## 具体日志及预测效果见jupyter文件
```
Epoch 50/150
187/187 [==============================] - 146s - loss: -0.2555 - main_output_loss: -0.5227 - aux_output_loss: 0.5344 - main_output_dice_coef: 0.5227 - aux_output_acc: 0.7200 - val_loss: 0.0510 - val_main_output_loss: -0.3890 - val_aux_output_loss: 0.8801 - val_main_output_dice_coef: 0.3890 - val_aux_output_acc: 0.5856
Epoch 51/150
187/187 [==============================]...
```