#基于RGBD摄像头的人体检测代码说明
----------
## 目录结构
RGBD_Human_Detection
|
|----depthVisualLization
|
|----Detection
|
|----RGB2Vec
|
|----Training_withDepth_64bit

## depthVisualLization
1. 功能介绍：将16bit的深度图片转化为伪彩图。
2.  运行方式：depthVisualLization.exe depth_image_path save_color_image_path depth_image_path为16bit的深度图片文件路径 save_color_image_path为要保存的伪彩色图像的存储路径

## Detection
1. 功能：在RGBD图像中检测出人的位置
2. 运行方式：detect.exe color_image_list depth_image_list model_path      color_image_list 是要检测彩色图像的路径list文件    depth_image_list是要检测深度图像的路径list文件（需和彩色图像文件一一对应） model_path训练出来的模型

##RGB2Vec
1. 功能介绍： 将原始所需用来训练的图像文件分别求出各个输入通道后打包成.vec格式的文件提供给训练程序
2. 运行方式：main.exe list_filename output_folder is_save_debug_image      list_filename是所有训练样本图像的list文件    output_folder是用来存储输出的vec文件目录 is_save_debug_image是标志是否保存计算出来的通道图像。若是1则通道图像会被保存在output_folder下，否则是0不保存

## Training_withDepth_64bit
1. 功能介绍： 由训练样本生成的vec文件来训练人体检测的模型
2. 运行方式： 修改Frontal_Training.cpp文件中的参数。
	 1. L23:训练的log文件
	 2. L27:负样本图片集的list文件
	 3. L33:保存的人体检测模型目录
	 4. L 68-72:训练的vec文件的位置
