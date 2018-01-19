# 1. 介绍

`Funtouch` 致力于为Android爱好者提供专业的ROM适配工具。

`Funtouch`由Android爱好者`FlowerToMe`于二零一八年一月十六日在FlymeOS释出的适配工具的基础上再次改动而成

[![License](https://img.shields.io/badge/License-Apache%20V2.0-blue.svg)](LICENSE)


# 2. 分支命名

开源项目的分支命名与Android版本对应,目前支持**Android 6.0**的机型适配，分支名为：`marshmallow-6.0`

目录结构如下所示: 

    Funtouch
     +-- manifest           项目清单
     +-- tutorials          教程文档
     +-- plugins            扩展插件，用于扩展已有功能
     +-- build              编译环境，用于构建和编译机型
     +-- tools              适配工具
     +-- Funtouch           Funtouch相关，内容定期更新
          +-- release       Funtouch的ROM包
          +-- overlay       资源覆盖
     +-- devices            机型目录
          +-- base          适配Funtouch需要的默认机型
          +-- xxxx          供开发者适配Funtouch的机型


# 3. 下载
通过 `wget -c https://github.com/FuntouchPatch/Funtouch_manifest/raw/marshmallow-6.0/repo -P $HOME/bin`
<br/>通过 `chmod a+rx $HOME/bin/repo`设置需要的权限
<br/>通过 `export PATH=$HOME/bin:$PATH`导入脚本的路径，或是重启电脑

通过`repo init`命令的`-b`参数, 选择需要下载的分支。
通过`repo sync`同步: 

    repo init -u https://github.com/FuntouchPatch/Funtouch_manifest -b marshmallow-6.0
    repo sync -c -j4

如果连接一直失败或下载代码过慢，则使用以下命令:

    repo init --repo-url https://github.com/FuntouchPatch/Funtouch_repo.git \
                -u https://github.com/FuntouchPatch/Funtouch_manifest.git \
                -b marshmallow-6.0 --no-repo-verify
                
    repo sync --no-clone-bundle -c -j4


# 4. 适配

<b>* 标准流程</b>

下载完成后, 在开源项目根目录, 执行以下命令初始化开发环境: 

    source build/envsetup.sh

创建一个新的机型工程的目录(以demo为例), 后续的移植都在机型目录完成。

    mkdir -p devices/demo
    cd devices/demo

按照如下步骤，完成一个新机型的适配：

    $ funconfig      	# 生成机型配置文件Makefile
    $ fun pullota	# 生成新机型目录
    $ fun autopatch	# 自动插桩
    $ fun updatezip	# 生成适配完成的ROM包


<b>* 冲突处理</b>

自动插桩可能会造成代码合并冲突。冲突会以下面的形式标注出来, 开发者需要在厂商的文件中手工解决这些冲突。

    <<<<<<< VENDOR
      原厂的代码块
    =======
      Funtouch的代码块
    >>>>>>> BOSP


<b>* 版本升级</b>

可以跟随官方发布的最新ROM包，将已经是适配完成的机型升级到最新版本：

    $ make cleanall
    $ make upgrade


# 5. 贡献代码

利用Github的Pull-Request机制，便可将内容变更发送给`FlowerToMe`审阅。

![image](github-pull-request.png)

- 首先，在github页面上，点击“Fork”，将Flyme的git库拷贝到自己账户
- 然后，对拷贝的git库进行修改，将内容变更提交到自己的账户
- 最后，在github页面上，点击"New pull request"，向`FlowerToMe`官方发起代码审阅


# 6. 其他

<b>* 问题求助与反馈</b>
- <p><a href="mailto:252761878@qq.com">252761878@qq.com</a></p>
- <p><a href="mailto:gesnagtome@foxmail.com">gesnagtome@foxmail.com</a></p>

