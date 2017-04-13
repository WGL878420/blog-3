# ubuntu 环境下开发配置

## 安装git

```
sudo apt-get install git
```

### 初始化SSH key

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

### 初始化git配置

```
git config --global user.name  "xxx"
git config --global user.email "xxx"
```

## sublime中文编辑支持配置

```
git clone https://github.com/lyfeyaj/sublime-text-imfix.git

cd ~/sublime-text-imfix

sudo cp ./lib/libsublime-imfix.so /opt/sublime_text/

sudo cp ./src/subl /usr/bin/

# 启动方法1
LD_PRELOAD=./libsublime-imfix.so subl

# 启动方法2
## 修改/usr/share/applications/sublime_text.desktop文件
### 将Exec=/opt/sublime_text/sublime_text %F修改为
Exec=bash -c 'LD_PRELOAD=/usr/lib/libsublime-imfix.so /opt/sublime_text/sublime_text' %F

### 将Exec=/opt/sublime_text/sublime_text -n修改为
Exec=bash -c 'LD_PRELOAD=/usr/lib/libsublime-imfix.so /opt/sublime_text/sublime_text' -n

```

## 安装atom编辑器

```
sudo apt-get install atom

```

## node.js开发环境设置

- 去官网下载node.js linux下的tar安装包 （下载编译好的安装包） [https://nodejs.org/en/](https://nodejs.org/en/)
- 安装node.js环境

```
//解压安xz装包成tar
 xz -d node-v6.3.1-linux-x64.tar.xz

//解压tar包
 tar -zxvf node-v6.3.1-linux-x64.tar

//将解压后的文件重命名为nodejs，再复制到 /opt/目录下

 sudo cp -a nodejs /opt/


//配置全局环境变量
 sudo gedit /etc/profile

//配置个人账户环境变量
gedit ~/.bashrc


//在文件的最末尾加上环境变量配置
export NODE_HOME=/opt/nodejs/bin
export NODE_PATH=/opt/nodejs/lib/node_modules
export PATH=$NODE_HOME:$PATH


//保存配置全局变量
sudo source /etc/profile

//保存个人账户环境变量
gedit ~/.bashrc

//配置国内镜像源
npm config set registry https://registry.npm.taobao.org

```

## 安装chrome浏览器

```
#!/bin/sh

sudo wget https://repo.fdzh.org/chrome/google-chrome.list -P /etc/apt/sources.list.d/

wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -

sudo apt-get update

sudo apt-get install google-chrome-stable

/usr/bin/google-chrome-stable
```
