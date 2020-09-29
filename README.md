# randomly-copy-namesake-labels-and-imgs
Solution on how to randomly copy nameske imgs and labels  using parts of COCO dataset 

In my process of learing YOLOv5, I find it difficult to use the whole COCO dataset because of its large size, So I try to use parts of COCO. Here is how I plan to randomly copy namesake labels and imgs from COCO. One can readily customize his/her own 'small COCO' by change the path and the rate you want to get.

import os
import random
import shutil

picture_fileDir = r"/path_1/"  # 源图片文件夹路径
picture_tarDir = r"/path_2/"  # 将图片移动到新的文件夹路径
label_fileDir = r"/path_3/"  # 源标签文件夹路径
label_tarDir = r"/path_4/"  # 将标签移动到新的文件夹路径

picture_pathDir = os.listdir(picture_fileDir)  # 取图片的原始路径
file_number = len(picture_pathDir)
rate = 0.1  # 自定义抽取图片的比例，比方说100张抽10张，那就是0.1
pick_number = int(file_number * rate)  # 按照rate比例从文件夹中取一定数量图片
sample = random.sample(picture_pathDir, pick_number)  # 随机选取pick_number数量的样本图片
print(sample)

for name in sample:
    print(name)
    shutil.copy(picture_fileDir + name, picture_tarDir + name)
    shutil.copy(label_fileDir + os.path.splitext(name)[0] + '.txt', label_tarDir + os.path.splitext(name)[0] + '.txt')
