## YOLOV3：You Only Look Once目标检测模型在Pytorch当中的实现
---

## 目录
1. [所需环境](#所需环境)
2. [文件下载](#文件下载)
3. [训练步骤](#训练步骤)
4. [预测步骤](#预测步骤)
5. [评估步骤](#评估步骤)
6. [Tensorboard可视化](#tensorboard可视化)


## 所需环境
操作系统：linux  torch == 1.2.0  

## 文件下载
训练所需的yolo_weights.pth可以在百度云下载。  
链接: https://pan.baidu.com/s/1hCV4kg8NyStkywLiAeEr3g   
提取码: 6da3 

VOC数据集下载地址如下，里面已经包括了训练集、测试集、验证集（与测试集一样），无需再次划分：  
链接:  https://pan.baidu.com/s/1fXg-h0YDihGqxSg_td_Zng?pwd=j7qk
提取码：j7qk
   
## 训练步骤
1. 数据集的准备   
**本文使用VOC格式进行训练，训练前需要下载好VOC07+12的数据集，解压后放在根目录**  

2. 数据集的处理   
运行voc_annotation.py生成根目录下的2007_train.txt和2007_val.txt。   

3. 开始网络训练   
train.py的默认参数用于训练VOC数据集，可以调整batchsize，learning rate，epoch等参数。设置完成后直接运行train.py即可开始训练。   
  

## 预测步骤  
### 使用自己训练的权重
1. 训练结果预测需要用到两个文件，分别是yolo.py和predict.py。   
**yolo.py文件中的model_path指向已训练好的权值文件，训练好的权值文件百度网盘链接:链接: https://pan.baidu.com/s/1Emdo9PRIrbz9JkTqlD8nFw?pwd=7mwx 提取码: 7mwx 
从百度网盘中下载训练好的权值文件并放在logs文件夹里。**

2. 运行predict.py进行检测，输入  
```python
img/street.jpg/jpeg,三张测试图片为catdog1.jpeg，railwaystaion.jpeg和test1.jpg
```

## 评估步骤 
### 评估VOC07+12的测试集
1. 运行get_map.py即可获得评估结果，评估结果会保存在map_out文件夹中。

## Tensorboard可视化
1. 训练后会在logs/loss_xx文件夹下生成events.out.tfevents.xxx文件。

2. 进入到logs/loss_xx文件夹下后输入tensorboard --logdir='log保存路径' --port=6006（远程连接端口以自己设置为准）

3. 运行以上命令后打开生成的网址即可查看利用Tensorboard可视化后的train loss和val loss曲线。

