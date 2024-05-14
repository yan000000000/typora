# 基本软件使用

## CubeMX基本使用

1. 打开cubeMX软件，在file选项中选择“New Project”

![image-20240427140721268](.assets/image-20240427140721268.png)

2. 搜索stm32f407ig，选择STM32F407IGHx芯片（即开发板C的控制芯片），双击后等待加载

![image-20240427140903187](.assets/image-20240427140903187.png)

3. 在System Core下选择RCC选项，在RCC Mode and Configuration选项中的High Speed Clock（HSE）下选择Crystal/Ceramic Resonator。这一步是为了选择外部晶振来充当我们的振荡源

![image-20240427141212099](.assets/image-20240427141212099.png)

4. 点击顶部的 Clock Configuration，进行主频配置；将 Input frequecncy 设置为 12，点击

旁边的 HSE 圆形按钮，配置/M 为/6，配置*N 为 X168，配置/P 为/2 ，选择 PLLCLK 圆形

按钮，配置 APB1 Prescaler 为/4，配置 APB2 Prescaler 为/2

![e058f09fff24669885c4dea03874588](.assets/e058f09fff24669885c4dea03874588.png)

![bc022a3cf6acc2ccefa3f3ffed2aefb1](.assets/bc022a3cf6acc2ccefa3f3ffed2aefb1.PNG)

5. 点击顶部的 Pinout & Configuartion，选择 SYS，在 Debug 下拉框中选择 Serial Wire；

![image-20240427141607557](.assets/image-20240427141607557.png)

6. 点击顶部的 Project Manager，给工程起名，选择存放目录，在 Toolchain/IDE 中选择 MDK

	ARM V5

![image-20240427141717516](.assets/image-20240427141717516.png)

![6582de4568538f128832bfc05e26017](.assets/6582de4568538f128832bfc05e26017.png)

7. 点击旁边的 Code Generator，勾选 Copy only the necessary library files 以及 Generate 

	peripheral initialization as a pair of ‘.c/.h’ files per peripheral；

![a9027a42ae7267441732e9018d83741d 2](.assets/a9027a42ae7267441732e9018d83741d 2.PNG)

8. 如果不需要打开并初始化其他接口，就可以导出了

![a9027a42ae7267441732e9018d83741d](.assets/a9027a42ae7267441732e9018d83741d.PNG)

## Keil入门

1. 认识界面

	1.打开生成的工程，keil 界面如图所示，其中 1 为调试模式，2 为编译改变的文件，3 为编

	译全部的文件，4 为下载按键，5 为工程设置选项，6 为工程目录；

![image-20240427142232685](.assets/image-20240427142232685.png)

2. 点击 5 工程设置，进行工程相关设置，选择 Output，其中 Create HEX file 为是否生成

	HEX 文件，Browse Information 为是否增加浏览信息，选择是，可以使用鼠标右键点击函数

	进行跳转操作，但会增加编译时长；

![image-20240427142419210](.assets/image-20240427142419210.png)

3. 点击 C/C++，其中 1 方框为工程宏定义设置，可在此添加宏定义；2 方框为头文件引用目

	录，对于项目自行建立的 h 文件需要在此处进行目录录入; 3 如果要支持c++，可以在此加上--cpp11

![image-20240427142458351](.assets/image-20240427142458351.png)

4. 点击 Debug 选项，设置好对应的下载器；

![image-20240427143658786](.assets/image-20240427143658786.png)

5. 点击下载器旁边的 Settings 选项，进行下载器相关设置，其中 Clock 中设置下载器的频

	率，频率越高，下载速度越快，但容易受到干扰；

![image-20240427143756099](.assets/image-20240427143756099.png)

6. 点击 Flash Download，其中 Erase Full Chip 代表下载时擦除芯片内全部页面的 flash，

	Erase Sectors 代表下载时擦除部分页面的 flash，Do not Erase 代表下载时不擦除 flash ；

	点击 Reset and Run 代表下载完程序后立即运行程序。

	![image-20240427143910303](.assets/image-20240427143910303.png)

![image-20240427143956731](.assets/image-20240427143956731.png)

### Keil调试

1. 在 keil 中编译之后，点击调试按键进入调试模式；

![image-20240427144106572](.assets/image-20240427144106572.png)

2. 进入调试模式后，可以选择 watch 窗口，watch 窗口可以参看变量的数值大小；

![image-20240427144238736](.assets/image-20240427144238736.png)

3. 可以在需要参看的变量点击右键，将其加入 watch 窗口；

![image-20240427144314524](.assets/image-20240427144314524.png)

4. 如果数据在程序运行中无变化，除了数据本身没有发生变化的场合，还可能由于未开启

	PeriodicWindows Update。

![image-20240427144429283](.assets/image-20240427144429283.png)

### Keil添加文件夹目录

[新建文件夹传送门](https://blog.csdn.net/MQ0522/article/details/128147014?spm=1001.2101.3001.6650.6&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-6-128147014-blog-45333165.235%5Ev43%5Epc_blog_bottom_relevance_base8&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-6-128147014-blog-45333165.235%5Ev43%5Epc_blog_bottom_relevance_base8&utm_relevant_index=7)

1. 第一步打开工程目录选项

![image-20240427162833440](.assets/image-20240427162833440.png)

2. 直接应用创建文件夹，添加文件（这里的添加文件不支持.h,.hpp头文件），删除文件，或者上移下移。注意这里只是创建keil的目录而不是实际文件夹。你还要自己在文件夹上移动进去。记得点OK，不要点X，不然不会保存

![image-20240427163025953](.assets/image-20240427163025953.png)

3. 头文件要到工程设置选项下添加，在最后一张图片的地方复制文件地址

![image-20240427163548589](.assets/image-20240427163548589.png)

![image-20240427163605334](.assets/image-20240427163605334.png)

![image-20240427163627109](.assets/image-20240427163627109.png)



