环境
操作系统：ubuntu 18.04
pyhton:3.6.9
cmake:
conan:
GCC:
git:

创建虚拟环境：
    mkdir pcl-1.9.1
    cd pcl-1.9.1
    python -m venv venv
    source venv/bin/acticate

安装环境：
sudo pyhton3 pip install conan

安装conan最新的证书：
conan config install https://github.com/conan-io/conanclientcert.git

设置仓库：
conan remote add conan-center https://center.conan.io
conan remote list #查看设置是否成功
conan-center: https://center.conan.io [Verify SSL: True]#查询到的仓库地址

拉取项目：
git clone https://github.com/bashbug/pcl-for-android.git

tips:
    修改boost源码下载，原地址已失效
        将conanfiles/boost/conanfile.py中
        tools.get("https://dl.bintray.com/boostorg/release/{}/source/{}.tar.gz".format(self.version, self.folder_name))
        替换为tools.get("https://boostorg.jfrog.io/artifactory/main/release/{}/source/{}.tar.gz".format(self.version, self.folder_name))

    修改PCL配置文件
        通过查conan仓库
            conan search eigen* -r=conancenter  
            Existing package recipes:

            eigen/3.3.7
            eigen/3.3.8
            eigen/3.3.9
            eigen/3.4.0
        将conanfiles/PCL/conanfile.py中
        self.requires"eigen/3.3.7@conan/stable替换为self.requires("eigen/3.3.7")

编译：
    armeabi-v7a：
        ./pcl-build-for-android.sh armeabi-v7a
    arm64-v8a
        ./pcl-build-for-android.sh arm64-v8a

参考文章:https://blog.csdn.net/brucemiao/article/details/122678742
        https://github.com/bashbug/pcl-for-android

