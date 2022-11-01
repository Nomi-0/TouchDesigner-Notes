# Cooking, Optimization, & SceneChanger

## Optimization

#### 1. cpu/gpu bound

cpu noise CHOP的channel长度
hog CHOP

gpu TOP的resolution
glsl的pixel shader

memory 
pixel format

解决cpu/gpu不够用的问题：
用脚本来指定工程跑在哪个cpu/gpu上
同一gpu 多线程
![image](https://user-images.githubusercontent.com/56717775/199144154-bf4c3553-967d-4bc4-9a43-d3acf86dc9f4.png)

如果你有多gpu，也可以指定不同gpu

Engine COMP
即多线程。自定义gpu还在开发

#### 优化方法
1. 在一些分辨率不影响结果的清空下可以适当降低分辨率
trace/blob track 可以考虑降低分辨率
2. transform SOP尽量提前，或者在geo COMP中执行
3. 改变op的顺序，把一直cooking的op放在尽可能后面
4. 善用Instancing，取代point SOP
