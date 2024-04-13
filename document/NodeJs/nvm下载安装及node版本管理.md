## nvm是什么？
- nvm全名node.js version management，顾名思义是一个nodejs的版本管理工具。通过它可以安装和切换不同版本的nodejs。下面列出下载、安装及使用方法。
## 下载
- 下载地址：[Releases · coreybutler/nvm-windows (github.com)](https://github.com/coreybutler/nvm-windows/releases)
-  nvm-noinstall.zip：绿色免安装版，但使用时需进行配置。
-  nvm-setup.zip：安装版，推荐使用
!![](../static/annex/Pasted%20image%2020240410210728.png)
## 安装
- 双击安装文件 nvm-setup.exe，nest
!![](../static/annex/Pasted%20image%2020240412195058.png)
- 选择nvm安装路径
!![](../static/annex/Pasted%20image%2020240412195232.png)
- 选择nodejs路径
!![](../static/annex/Pasted%20image%2020240412195327.png)
- 确认安装即可
!![](../static/annex/Pasted%20image%2020240412195423.png)
## nvm配置
### 环境变量配置
点击电脑-属性–高级系统设置-环境变量
用户变量和环境变量都需要新建2个环境变量：
- 点击新建-变量名输入NVMHOME-变量值输入D:\nvm（即：nvm安装路径）
- 点击新建-变量名输入NVMSYMLINK-变量值输入D:\nodeJs（即：nodeJs路径）
!![](../static/annex/Pasted%20image%2020240412195949.png)
- 选择Path，后面追加【%NVMHOME%】、【%NVMSYMLINK%】属性变量
!![](../static/annex/Pasted%20image%2020240412200000.png)
### 安装完确认
- 打开CMD，输入命令 nvm ，安装成功则如下显示。
!![](../static/annex/Pasted%20image%2020240412195531.png)
### nvm配置淘宝镜像
- 打开cmd窗口 ,输入以下命令
```bash
nvm node_mirror https://npm.taobao.org/mirrors/node/
nvm npm_mirror https://npm.taobao.org/mirrors/npm/
```
- 进入nvm安装路径下，打开setting.txt文件，显示如下
!![](../static/annex/Pasted%20image%2020240412200509.png)
##### 由于淘宝镜像到期，已更换其他镜像
```
nvm node_mirror https://npmmirror.com/mirrors/node/
nvm npm_mirror https://npmmirror.com/mirrors/npm/
```

## 安装完成
### nvm常用命令
```bash
nvm list //展示本地安装的所有版本，*号表示当前正在用
nvm install [版本号] //安装指定版本node 例如： nvm install 12.18.0
nvm use 12.18.0 //使用特定版本
nvm uninstall 12.18.0 //卸载指定版本
```
## 安装/管理node
### nvm下载node
- 打开cmd窗口，输入命令：
```
nvm install 12.19.0
```
- 安装完成
!![](../static/annex/Pasted%20image%2020240412201512.png)
下载完成后输入：
```
nvm use 12.19.0 //必须有输入这行命令后，node命令才会生效

/*检查node是否安装成功*/
node -v
npm -v
```
!![](../static/annex/Pasted%20image%2020240412201650.png)
## node环境配置
- 还记得安装nvm时设置的nodeJs目录嘛？此目录是作为软连接目录，存放nvm当前指向node版本的内容，下面我们设置node的相关变量时都会基于此目录，这样nvm切换node不同版本时不会影响node环境变量
### 配置全局目录
- 在nodeJS目录下手动创建全局文件存放目录node_global和缓存目录node_cache
- cmd命令窗口输入
```
npm config set prefix "P:\**\nodeJs\node_global"
npm config set cache "P:\**\nodeJs\node_cache"
```
!![](../static/annex/Pasted%20image%2020240412202203.png)
## 命令提示
`nvm arch` ：显示node是运行在32位还是64位。
`nvm install <version> [arch]` ：安装node， version是特定版本也可以是最新稳定版本latest。可选参数arch指定安装32位还是64位版本，默认是系统位数。可以添加--insecure绕过远程服务器的SSL。
`nvm list [available] `：显示已安装的列表。可选参数available，显示可安装的所有版本。list可简化为ls。
`nvm on` ：开启node.js版本管理。
`nvm off` ：关闭node.js版本管理。
`nvm proxy [url]` ：设置下载代理。不加可选参数url，显示当前代理。将url设置为none则移除代理。
`nvm node_mirror [url]` ：设置node镜像。默认是https://nodejs.org/dist/。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。
`nvm npm_mirror [url] `：设置npm镜像。https://github.com/npm/cli/archive/。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。
`nvm uninstall <version>` ：卸载指定版本node。
`nvm use [version]` [arch] ：使用制定版本node。可指定32/64位。
`nvm root [path]` ：设置存储不同版本node的目录。如果未设置，默认使用当前目录。
`nvm version` ：显示nvm版本。version可简化为v。