# license-plate-detect-recoginition-opencv
使用opencv部署深度学习车牌检测与识别
python版本的主程序是detect_rec_img.py，c++版本的主程序是main.cpp

由于opencv无法在图片上写汉字，因此在C++版本的程序里，把车牌识别结果在终端打印

注意，我在opencv4.5.1的环境里编写的c++程序能编译运行，
但是换一台电脑，opencv环境是4.5.0的，程序运行出错了，因此opencv版本最好是安装目前最新的4.5.1


车牌里文字长度是固定的7个字，而身份证里的文字有多段，有些文字的长度不是固定的，例如姓名，地址。
一次你相比于身份证信息识别，车牌文字识别要简单多了。
对于车牌识别模块，可以更换成crnn网络做识别，也可以更换到传统图像处理方法分割字符后逐个字符识别


需要注意的是，在我的github仓库里发布了另一套深度学习车牌检测与识别，只不过那个是基于pytorch框架做的，
这两套程序除了依赖库不相同，还有一个不同之处就是在车牌检测模块里的输入图片的预处理方式。在基于pytorch框架的程序里，
输入图片是动态尺寸的，但是在基于opencv的程序里，输入图片是resize到固定尺寸的。起初我也想过生成onnx文件使opencv程序
支持动态输入尺寸，然而在运行程序时出错了。这个踩坑的详细记录，可以阅读我的博客文章  https://blog.csdn.net/nihate/article/details/115504611

考虑到车牌是一个宽度远大于高度，因此在基于opencv的程序里，对图片做resize是保持高宽比的resize
