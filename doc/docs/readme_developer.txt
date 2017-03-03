1 jdk安装
	1) 下载：jdk-6u45-linux-x64.bin 到/work/tools目录下
        (无此目录自行创建,命令  mkdir /work/tools)
	2) 赋予执行权限,命令如下:
	    chmod +x jdk-6u45-linux-x64.bin
	3) 执行jdk的安装. 
	    ./jdk-6u45-linux-x64.bin
    4) 配置环境变量.
        修改~/.bashrc文件来配置环境变量

        vim ~/.bashrc
        在用户目录./bashrc中添加
        export JAVA_HOME=/work/tools/jdk1.6.0_45
        export PATH=$PATH:$JAVA_HOME/bin
 
    5) java -version检查安装是否成功.
        成功显示如下信息:

        java version "1.6.0_45"
        Java(TM) SE Runtime Environment (build 1.6.0_45-b06)
        Java HotSpot(TM) 64-Bit Server VM (build 20.45-b01, mixed mode)

2  开发工具eclipse安装
    1) 下载 adt-bundle-linux-x86_64-20140702.zip
    2) 解压到/work/tools/,一个目录为eclipse 一个为sdk
    3) 进入eclipse目录, eclipse文件启动程序

3  SDK配置(承接2)
    1) sdk 位于目录/work/tools/adt-bundle-linux-x86_64-20140702
    2) 修改~/.bashrc文件来配置环境变量

        vim ~/.bashrc
        在用户目录./bashrc中添加
        export SDK_HOME="/work/tools/adt-bundle-linux-x86_64-20140702/sdk"
        export PATH=$SDK_HOME/platform-tools:$SDK_HOME/tools:$SDK_HOME/build-tools/android-4.4W:$PATH
    3) 任意目录下面输入adb验证sdk有无配额成功

4 android adb 命令使用
	adb help			查看adb命令的帮助信息
	adb devices 			显示当前连接设备或启动的模拟器
	adb logcat 			查看LOG信息
	adb logcat -s 标签名		按照标签名来过滤LOG信息
	adb logcat | tee /tmp/log	查看log信息并保存到文件/tmp/log
	adb remount			重新挂在分区,使系统分区可读写
	adb install -r apk包		安装apk/data/app
	adb uninstall  apk包的包名	卸载install的apk
	adb push apk包 /system/app 	把apk写到车机/system/app

	adb shell			删除/system/app下的apk包(push过的或系统自带)
	cd /system/app
	rm /apk包
	exit

	adb pull <remote> <local>	获取车机<remote>文件到本地<local>
	adb shell reboot		车载系统重启

5 git 使用
    git 配置

        编辑./bash/git_config.sh, 修改自己用户名和邮箱
        执行
        chmod +x ./bash/git_config.sh 
        . ./bash/git_config.sh

	简单介绍几个常用命令(详情查看结尾学习网站)
	git --help			查看git帮助命令
	git 几个阶段 1工作目录  	2缓存区 	3本地仓库 	4远程仓库	
	1)	创建本地仓库(直接拷贝的代码一般默认有本地仓库不需要创建)
		(1) 无远程仓库	git init
		(2) 有远程仓库	git clone <remote> -b <branch>
	2)	查看本地修改
		git diff
	3)	撤销本地修改
		git checkout filename
	4)	本地文件或修改添加到缓存区
		git add filename
	5)	缓存区的内容恢复到本地修改
		git reset filename
	6)	将缓存区提交到本地仓库(-m 后面跟提交信息)
		git commit -m "提交信息"


部分学习网站
	猴子都能懂的git入门：http://backlogtool.com/git-guide/cn/intro/intro1_1.html
	Android开发工具集合：http://www.androiddevtools.cn/index.html
	免费的编程中文书籍索引：https://github.com/justjavac/free-programming-books-zh_CN
