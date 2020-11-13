简体中文 | [English](https://github.com/PUANEY/OnlineJudgeDeploy/blob/master/README.en.md)

## 环境准备

### Linux 环境

1. 安装必要的依赖(推荐使用root用户登录并运行以下命令，否则前面加sudo)

    ```bash
    sudo apt-get update && sudo apt-get install -y vim python3-pip curl git
    pip3 install --upgrade pip -i http://pypi.douban.com/simple --trusted-host pypi.douban.com
    pip3 install docker-compose -i http://pypi.douban.com/simple --trusted-host pypi.douban.com
    ```

2. 安装 Docker 

    国内用户使用脚本一键安装: `sudo curl -sSL https://get.daocloud.io/docker | sh`  
    国外用户使用脚本一键安装: `sudo curl -sSL get.docker.com | sh`
    
    详细步骤参照： [https://docs.docker.com/install/](https://docs.docker.com/install/)

### Windows 环境


Windows 下的安装仅供体验，勿在生产环境使用。如有必要，请使用虚拟机安装 Linux 并将 OJ 安装在其中。

以下教程仅适用于 Win10 x64 下的 `PowerShell`

1. 安装 Windows 的 Docker 工具
2. 右击右下角 Docker 图标，选择 Settings 进行设置
3. 选择 `Shared Drives` 菜单，之后勾选你想安装 OJ 的盘符位置（例如勾选D盘），点击 `Apply`
4. 输入 Windows 的账号密码进行文件共享
5. 安装 `Python`、`pip`、`git`、`docker-compose`，安装方法自行搜索。

## 开始安装

1. 请选择磁盘空间富余的位置，运行下面的命令

    ```bash
    git clone https://github.com/PUANEY/OnlineJudgeDeploy.git && cd OnlineJudgeDeploy
    ```

2. 启动服务

    ```bash
    docker-compose up -d
    ```

根据网速情况，大约5到30分钟就可以自动搭建完成，全程无需人工干预。

等命令执行完成，然后运行 `docker ps -a`，当看到所有的容器的状态没有 `unhealthy` 或 `Exited (x) xxx` 就代表 OJ 已经启动成功。

## 更改前端文件
1. 从`OnlineJudgeFE`中build出`dist`文件夹: `npm run build`或者直接打开网页下载`https://github.com/PUANEY/OnlineJudgeFE/releases/download/oj1.0/dist.zip`后解压。
2. 切换到backend目录: `cd OnlineJudgeDeploy && cd data && cd backend`。
3. 将`dist`文件夹替换掉。
4. 重启后端：`docker restart jhoj-backend`。

## 尽情享用吧

通过浏览器访问服务器的 HTTP 80 端口或者 HTTPS 443 端口，就可以开始使用了。后台管理路径为`/admin`, 安装过程中自动添加的超级管理员用户名为 `root`，密码为 `rootroot`， **请务必及时修改密码**。


## 定制
若需要对系统进行修改或二次开发，请参照各模块的**README**，修改完成后需自行构建Docker镜像并修改`docker-compose.yml`

## 遇到了问题？

QQ群：`858114474`
