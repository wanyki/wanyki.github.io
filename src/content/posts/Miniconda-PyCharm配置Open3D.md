---
title: Miniconda+PyCharm配置Open3D
published: 2025-07-16 07:38:34
tags: [Open3D]
author: yuechu
---

#### 1.下载[Miniconda](https://www.anaconda.com/download/success)

![pV1fixP.png](https://s21.ax1x.com/2025/07/16/pV1fixP.png)



#### 2.安装时注意选择添加path

#### 3.使用Anaconda Prompt



![pV1fP2t.png](https://s21.ax1x.com/2025/07/16/pV1fP2t.png)



#### 4.创建虚拟环境

```bash
conda create -n python38 python=3.8		#创建一个python版本为3.8并且名为python38的虚拟环境
```

#### 5.激活虚拟环境

```bash
activate python38
```

#### 6.配置PyCharm,添加解释器（注意选择当时命名的python38）



![pV1fC8I.png](https://s21.ax1x.com/2025/07/16/pV1fC8I.png)



![pV1f9PA.png](https://s21.ax1x.com/2025/07/16/pV1f9PA.png)



#### 7.测试代码，点击然后下载 [bun_zipper.ply](https://github.com/google/draco/blob/main/testdata/bun_zipper.ply)，然后把 [bun_zipper.ply](https://github.com/google/draco/blob/main/testdata/bun_zipper.ply)放入项目目录

```python
import open3d as o3d
import numpy as np
print("read the point cloud ,print it and render it")
p = o3d.io.read_point_cloud("bun_zipper.ply")
print(p)
print(np.asarray(p.points))
o3d.visualization.draw_geometries([p])
```

因为一开始没有下载open3d跟numpy，可以根据IDE报错提示下载或者使用终端（我没有使用终端，但是效果应该一样）



![pV1fS5d.png](https://s21.ax1x.com/2025/07/16/pV1fS5d.png)



```python
pip install open3d
conda install numpy
```
#### 8.正确结果



![pV1fkKf.png](https://s21.ax1x.com/2025/07/16/pV1fkKf.png)


