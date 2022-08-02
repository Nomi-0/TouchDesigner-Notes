### [Reference](https://blog.csdn.net/qq_43219379/article/details/123129973)
## python pip
1. 安装python https://www.youtube.com/watch?v=Kn1HF3oD19c  要关闭vpn！
2. 安装pip和虚拟环境depth https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/ （注意py换成D:\python37\python.exe）
**之后的步骤都在虚拟环境中完成**

## transformers
3. 进入虚拟环境安装transformers https://huggingface.co/docs/transformers/installation
```
depth\Scripts\activate # 进入虚拟环境
```

## pytorch 
4. 之后要安装pytorch，先查看cuda版本

![image](https://user-images.githubusercontent.com/56717775/182333421-ee74ecfb-aaf8-499d-8d62-291fa0f67360.png)

5. 在https://pytorch.org/get-started/locally/#start-locally 找到对应cuda的下载命令 但是一直报错下不了

6. follow[这个教程](https://blog.csdn.net/weixin_51756104/article/details/124398722)，先下载三个文件，再pip install+安装包的路径安装，如下
```
pip install C:\Users\A\Desktop\
pip install C:\Users\A\Desktop\torchvision-0.13.0+cu116-cp37-cp37m-win_amd64.whl
pip install C:\Users\A\Desktop\
```

7. 测试pytorch
```
python
import torch
x = torch.rand(3)
print(x)
torch.cuda.is_available()
```

## cuda cudnn 
[查看版本](https://blog.csdn.net/weixin_61995249/article/details/124069914)
8. 安装方法见[这个教程](https://blog.csdn.net/weixin_51756104/article/details/124398722)
