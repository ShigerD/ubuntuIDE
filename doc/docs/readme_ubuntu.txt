1 进入Terminal
    快捷键 Ctrl+Alt+T 
    或者
    点击系统左上角 开始菜单(Dash home), 输入Terminal即可匹配到,点击进入

2 cd 进入目录

    如  cd /work/   进入work目录
        cd ~        进入用户目录
        cd ..       进入上以一级目录
        cd -        进入上次停留目录

3 自动补全
    在shell下, 输入任意字符,按Tab均可以进行目录或命令补全

4 可视化编辑器gedit 
    shell下
    gedit 文件路径
    或
    开始菜单 输入gedit打开,点击 Text Editor打开编辑器

5 查找文件
    find ./ -name main.java 在当前目录下查找main.java文件
    其它功能 find --help 或网络查询

6 搜索包含特定字符串的文件
    grep -rn "test" ./      在当前目录下搜索包含字符串"test"的文件
    其它功能 grep --help 或网络查询
