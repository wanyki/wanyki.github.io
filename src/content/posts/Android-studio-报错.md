---
title: Android studio 报错
published: 2024-02-08 13:19:05
tags: [Android studios]
---

# The emulator process for AVD Pixel_2_API_30 has terminated.

# 错误代码1073740791 (0xC0000409)

这个问题的解决办法在网上有很多种办法，但是对于我来说都不使用，所以查看自己的studio的log文件，如果你是跟我一样的问题，可以尝试我这种办法，

#### log文件路径

```
C:\Users\[你自己的用户名]\AppData\Local\Google\AndroidStudio2023.1\log
```

##### 根据你最后一次出现错误的时间找log，如果你有这一种错误的话

```
 Emulator: Pixel 2 API 30 - Process finished with exit code -1073740791 (0xC0000409)
```

![](https://img.yuechucard.space/blog/AndroidStudio/1.png)

##### 就意味着这是由于显卡驱动(反正就是跟显卡原因有关),这时候打开studio，新建一个虚拟机在第三步的时候点击红色方框，下拉选择software

![](https://img.yuechucard.space/blog/AndroidStudio/2.png)

##### 但是有的人这个选项框是灰的，选择不了，就比如我，这个时候跳到下一步（如果你不是灰的，能选择的话就不用后面的步骤了）

##### 打开你的虚拟机文件，如图

![](https://img.yuechucard.space/blog/AndroidStudio/3.png)

![](https://img.yuechucard.space/blog/AndroidStudio/4.png)

![](https://img.yuechucard.space/blog/AndroidStudio/5.png)

##### 右键config.ini，选择编辑，找到以下两项并修改

```
hw.gpu.enabled = yes
hw.gpu.mode = software #这个地方一开始应该是等于auto,把auto改成software
```

##### 关闭文件的时候别忘保存，再重新打开studio，打开虚拟机应该就行了

#### PS：我估计这个问题是AMD芯片或者显卡的锅，烦死了，搞了一整天
