# 全新环境安装transformers全流程记录

### 配置
python === 3.7.11
pytorch === 1.12.0
cuda cudnn === 11.6
transformers

### [Reference](https://blog.csdn.net/qq_43219379/article/details/123129973)
## python pip
1. 安装python https://www.youtube.com/watch?v=Kn1HF3oD19c  要关闭vpn！
2. 安装pip和虚拟环境depth https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/ （注意py换成D:\python37\python.exe）

**之后的步骤都在虚拟环境中完成**

## transformers
3. 进入虚拟环境安装transformers 

https://huggingface.co/docs/transformers/installation

```
depth\Scripts\activate # 进入虚拟环境
```

## pytorch

**关闭vpn**

4. 之后要安装pytorch，先查看支持的最高cuda版本

![image](https://user-images.githubusercontent.com/56717775/182333421-ee74ecfb-aaf8-499d-8d62-291fa0f67360.png)

5. 在https://pytorch.org/get-started/locally/#start-locally 找到对应cuda的下载命令 但是一直报错下不了

6. follow[这个教程](https://blog.csdn.net/weixin_51756104/article/details/124398722)，先下载三个文件，再pip install+安装包的路径安装，如下
```
pip install C:\Users\A\Desktop\  +文件名
```
装torchvision时报错，要删除代理

解决方法参考：[pip install 由于目标计算机积极拒绝，无法连接](https://blog.csdn.net/lezeqe/article/details/94913345?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-94913345-blog-103959039.pc_relevant_show_downloadRating&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-94913345-blog-103959039.pc_relevant_show_downloadRating&utm_relevant_index=1)

![image](https://user-images.githubusercontent.com/56717775/182509712-210ef5ed-72d2-412a-beb7-f5d01233661e.png)
![image](https://user-images.githubusercontent.com/56717775/182509798-a1b1526b-3d75-4366-bc9b-d9adb83f83bc.png)
![image](https://user-images.githubusercontent.com/56717775/182510140-8529a9e6-3593-4797-968d-6d20d531b955.png)

7. 测试pytorch
**安装结果**
![image](https://user-images.githubusercontent.com/56717775/182510329-cd9e36ac-3c07-4727-b887-18e4c7e57ec5.png)

```
python
import torch
x = torch.rand(3)
print(x)
torch.cuda.is_available()
```

## cuda cudnn 
[查看版本](https://blog.csdn.net/weixin_61995249/article/details/124069914)

8. 安装cuda和cudnn [添加环境变量 检查安装结果](https://www.cnblogs.com/zhaoyingjie/p/16066774.html)

[cuda地址](https://developer.nvidia.com/cuda-11-6-2-download-archive?target_os=Windows&target_arch=x86_64&target_version=11&target_type=exe_local)

![image](https://user-images.githubusercontent.com/56717775/182505839-2873b743-150d-46c4-af97-9afc2f8fa3da.png)

[cudnn地址](https://developer.nvidia.com/rdp/cudnn-download)

![image](https://user-images.githubusercontent.com/56717775/182505862-e8999806-b82e-47a7-ba65-c9859ec8e481.png)

![image](https://user-images.githubusercontent.com/56717775/182505996-e60c45a6-ae89-499c-b3f4-3464310388ec.png)


# transformers
pip install transformers

报错

![image](https://user-images.githubusercontent.com/56717775/182522669-5d582fd6-12a2-4cf7-9779-2ebb3d0d96ca.png)

[解决方法](http://www.snailtoday.com/archives/9467)
```
# 在最前面加上代码
import os
os.environ['NO_PROXY'] = 'stackoverflow.com'
```

# sublime python配置
[Sublime text 3搭建Python开发环境及常用插件安装](https://www.cnblogs.com/xinxin1994/p/10145847.html)

```
{
    "cmd": ["D:/Anaconda3/python.exe","-u","$file"], # 注意将地址换成虚拟环境depth里的exe
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python",
}
```

测试代码，下载模型需要翻墙
```
from transformers import pipeline

classifier = pipeline("sentiment-analysis")  # 情感分析
classifier("I've been waiting for a HuggingFace course my whole life.")
```

**测试结果**
![image](https://user-images.githubusercontent.com/56717775/182523250-094fb7b9-1662-461b-a10c-ebac6c243a89.png)

# 测试深度图代码

[下载模型](https://blog.csdn.net/weixin_41862755/article/details/120686480)

[python 报错 requests.exceptions.ConnectionError: HTTPSConnectionPool(host=‘huggingface.co‘,port=443):M](https://xat-suda.blog.csdn.net/article/details/120686319?spm=1001.2101.3001.6650.8&utma_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~default-8-120686319-blog-111386239.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~default-8-120686319-blog-111386239.pc_relevant_default&utm_relevant_index=12)
