# # 虚拟机安装Ubuntu

### 准备

1. 下载安装VMware Workstation（VM17）
    
2. Ubuntu镜像（Ubuntu20.04）
### 安装
#### 新建虚拟机
- 打开VMware17，创建新虚拟机，并选择典型安装

![](../static/annex/Pasted%20image%2020230624203959.png)

- 点击浏览，选择下载好Ubuntu系统镜像，点击下一步
![](../static/annex/Pasted%20image%2020230624203900.png)
- 输入用户名，进行下一步
![](../static/annex/Pasted%20image%2020230624204207.png)
- 设置名称及选择安装的位置，进行下一步
![](../static/annex/Pasted%20image%2020230624204410.png)
- 设定磁盘大小，选择将虚拟磁盘存储为单个文件，进行下一步
![](../static/annex/Pasted%20image%2020230624204512.png)
- 自定义硬件，设定好之后，点击完成
![](../static/annex/Pasted%20image%2020230624204620.png)
![](../static/annex/Pasted%20image%2020230624204746.png)
#### 开启虚拟机
- 点击开启此虚拟机，等待安装
![](../static/annex/Pasted%20image%2020230624204916.png)
- 点击登录
![](../static/annex/Pasted%20image%2020230624210035.png)
![](../static/annex/Pasted%20image%2020230624210128.png)
- 关闭，设置网络
![](../static/annex/Pasted%20image%2020230624211352.png)
#### 配置
###### - 设置为中文
![](../static/annex/Pasted%20image%2020230624210223.png)
![](../static/annex/Pasted%20image%2020230624211631.png)
![](../static/annex/Pasted%20image%2020230624211817.png)
- 选择
![](../static/annex/Pasted%20image%2020230624211946.png)
![](../static/annex/Pasted%20image%2020230624212053.png)
![](../static/annex/Pasted%20image%2020230624212449.png)
- 如果这时不能设置，先设置时区
![](../static/annex/Pasted%20image%2020230624212747.png)
###### - 设置时区
- 打开设置，选择date & time，设置Time Zone
![](../static/annex/Pasted%20image%2020230624213421.png)
- 选择东八区，如果看不到关闭按钮，先进行分辨率的设置
![](../static/annex/Pasted%20image%2020230624214031.png)
###### - 设置分辨率
- 打开终端，安装open-vm-tools
![](../static/annex/Pasted%20image%2020230624214225.png)
- 更新系统源
```bash
sudo apt-get update
```
![](../static/annex/Pasted%20image%2020230624214419.png)
- 安装open-vm-tools
```bash
sudo apt-get install open-vm-tools
```
![](../static/annex/Pasted%20image%2020230624214555.png)
- 安装完毕后再次回到设置时区设置
![](../static/annex/Pasted%20image%2020230624214724.png)
- 再次回到设置语言设置页
![](../static/annex/Pasted%20image%2020230624214821.png)
- 点击重启
![](../static/annex/Pasted%20image%2020230624214833.png)
- 设置中文完毕
![](../static/annex/Pasted%20image%2020230624215015.png)
- 改完中文键盘
![](../static/annex/Pasted%20image%2020230624210551.png)
![虚拟机/annex/Pasted image 20230624210643.png](%E8%99%9A%E6%8B%9F%E6%9C%BA/annex/Pasted%20image%2020230624210643.png)
![虚拟机/annex/Pasted image 20230624210706.png](%E8%99%9A%E6%8B%9F%E6%9C%BA/annex/Pasted%20image%2020230624210706.png)

![](../static/annex/Pasted%20image%2020230624210803.png)
###### - 跨系统复制粘贴
- 安装open-vm-tools-desktop，实现虚拟机和物理机之间的文件相互拖拽和复制、粘贴
```bash
sudo apt-get remove open-vm-tools-desktop -y
```
```bash
sudo apt-get install open-vm-tools-desktop
```
###### -  更改Ubuntu软件源
![](../static/annex/Pasted%20image%2020230624220950.png)
- 选择下载自：其他站点
![](../static/annex/Pasted%20image%2020230624221153.png)