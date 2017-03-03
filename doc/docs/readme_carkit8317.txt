1 项目环境搭建
    1) 下载项目build.tar.bz2包并解压到/work/目录下
        双击解压或tar -jxvf build.tar.bz2
    2) 配置mtk工具包, 解压mtk_tooks.tar.bz2到/work/tools/,
        tar -jxvf mtk_tools.tar.bz2
        进入mtk目录, 根据lrl_readme.txt进行安装
    3) 进入/work/build目录下,执行ln -s ./build/build.env selfenv 

2 关于编译
    1) 安装编译必要包
        sudo apt-get install flex bison gperf libesd0-dev libwxgtk2.6-dev zlib1g-dev build-essential libx11-dev libncurses5-dev genext2fs u-boot-tools git

        sudo apt-get install git gnupg flex bison gperf build-essential  zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386  libgl1-mesa-dev g++-multilib mingw32 tofrodos  python-markdown libxml2-utils xsltproc zlib1g-dev:i386 libzip-dev
    2) 在编译任何模块之前需要先进入/work/build/执行
    source ./selfenv
    3) 应用目录在build根目录下的./packages/apps下面
        方法一, 任何目录下如果包含有Android.mk说明此目录是一个模块或一个应用的根目录,可以在含有Android.mk的目录下
        执行 mm 命令既可以编译
        方法二, 在build根目录下执行
            mmm ./packages/apps/app名字
    4) 编译出来的apk或jar,就可以使用adb相关命令安装或push到设备上进行调试
       如执行 mmm ./packages/apps/Music
       编译结束,有如下信息
       Install: out/target/product/ac8317/system/app/Music.apk 
       则目录out/target/product/ac8317/system/app/下Music.apk即编译出来的apk
       可以通过以下命令安装
            adb install -r out/target/product/ac8317/system/app/Music.apk
       也可以通过以下命令push到设备中
            adb push out/target/product/ac8317/system/app/Music.apk /system/app

3.DNJ文件服务器
	内网 http://192.168.16.220:5000/webman/index.cgi
	外网 http://ext.digienginetek.com:5000/webman/index.cgi
	用户名	yinchangming
	密码	android

4.升级包制作、配置工具
	DNJ文件服务器：AN2_Utils -> Tools->配置编辑工具等

5.update.zip升级包
	DNJ文件服务器：An2Daily（每天版本） An2Release(正式版本)

6.格式化hd
	升级的时候在sdcard/udisk根目录放空文件format_hd

7.进入工厂模式
	1) 设置-->工厂设置-->密码8317-->工厂模式-->密码8888
	2) 拨号盘界面输入*#*#9527#*#*(部分系统需要在蓝牙连接之后操作)-->密码8888

8.校准
	1)无屏幕厂商id的车机，
		(1) 开机发现/bootlogo/config/calibrate/无校准文件，会自动弹出屏幕校准程序。
		(2) 三点或三点之上长按屏幕5s之上，会主动弹出屏幕校准程序。
	2) 有屏幕厂商id的车机（如爱民）
		在u盘根目录放calibrate_confirm文件，三点或三点之上长按屏幕5s之上，会主动弹出屏幕校准程序。

    注意: 查看有无屏幕厂商id,可以进入工厂模式-->屏参信息查看

9.蓝牙自动化测试（借助wince测试母机）
	1) 在sdcard/udisk1/udisk2根目录放bt_address文件，文件内容为测试母机地mac地址（如AA:BB:CC:DD:EE:FF）
	2) 在工厂设置中打开"蓝牙测试"即可进行自动化测试。

10.打开usb调试
	1) 进入工厂模式，进入"应用开关"，打开"USBSwitch",退出保存！
	2) 进入应用USBSwitch，选择USB Device,点ok。
	3) 连上usb即可调试（两个usb，有一个可以用）

11.打开自动保存log到sdcard/udisk
	1) 拨号盘输入*#*#1235789#*#*,进入开发者选项
	2) 日志存储位置，选择存储位置sdcard/udisk
	3) 勾选"Logcat调试"（即可保存上层log和内核logo到选择的路径）

12.目前获取emmc id的方式有两种：
    1) 通过工厂模式去获取，工厂模式===》6.设备编号===》保存到sd卡，  写入sd的emmc_id.txt文件中。
    2) 在升级前， 放入一个空的mmc_cid.txt到升级介质中， 升级时自动将emmc的ID写入到升级介质中的emmc_cid.txt文件中。

13.Reset复位孔功能介绍
    连续按MCU的RESET复位孔4次（间隔1S左右），解除MCU与安卓的握手保护。
    连续按MCU的RESET复位孔8次（间隔1S左右），MCU通知安卓进入强制升级。
    连续按MCU的RESET复位孔10次（间隔1S左右），MCU自己进入强制升级MCU状态。
    按MCU的RESET复位孔，MCU等同于断了一次B+。
