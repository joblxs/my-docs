## Git安装
#### Git下载
- Git官网下载，下载地址[Git - Downloading Package (git-scm.com)](https://git-scm.com/download/win)
#### Git安装
- 协议内容，直接next
!![](../static/annex/Pasted%20image%2020230626214912.png)
- 点击Browse选择存放的路径
!![](../static/annex/Pasted%20image%2020230626215121.png)
- 勾选相关哦配置
!![](../static/annex/Pasted%20image%2020230626215828.png)
- 直接next
!![](../static/annex/Pasted%20image%2020230626215931.png)
- 选择Git默认编辑器
!![](../static/annex/Pasted%20image%2020230626215952.png)
- 创建新项目时的分支名，默认master
!![](../static/annex/Pasted%20image%2020230626220001.png)
- 调整path环境变量
!![](../static/annex/Pasted%20image%2020230626220256.png)
- 选择ssh执行文件
!![](../static/annex/Pasted%20image%2020230626220334.png)
- 选择https后端传输
![](Pasted%20image%2020230626220438.png)
- 配置行尾符号转换
!![](../static/annex/Pasted%20image%2020230626220508.png)
- 配置终端模拟器以与 Git Bash 一起使用
!![](../static/annex/Pasted%20image%2020230626220527.png)
- 选择默认git pull行为
!![](../static/annex/Pasted%20image%2020230626220624.png)
- 选择一个凭证帮助程序
!![](../static/annex/Pasted%20image%2020230626220705.png)
- 配置额外的选项
!![](../static/annex/Pasted%20image%2020230626220755.png)
- 配置实验性选项
!![](../static/annex/Pasted%20image%2020230626220829.png)
- 等待安装完成
!![](../static/annex/Pasted%20image%2020230626220854.png)
## Git配置
#### 检查Git
- 查看是否安装成功
```bash
git --version
```
!![](../static/annex/Pasted%20image%2020230626221245.png)
- 查看Git是否添加到系统变量中
```bash
echo $PATH
```
!![](../static/annex/Pasted%20image%2020230626221458.png)
#### 配置Git
- 配置用户名
```bash
git config --global user.name "username" //（"username"是自己的账户名）
```
- 配置邮箱
```bash
git config --global user.email "123@email.com" //("123@email.com"注册账号时用的邮箱)
```
!![](../static/annex/Pasted%20image%2020230626222320.png)
- 查看是否配置成功
```bash
git config --global --list
```
#### 生成SSH
```text
SSH（Secure Shell）是一种加密的网络协议，用于在不安全的网络中安全地传输数据。它主要用于远程登录、远程执行命令、传输文件等操作，可以让用户通过不安全的网络连接到远程计算机，并在远程计算机上执行各种操作，而不必担心数据被窃取或篡改。

SSH 协议使用了公钥加密算法和对称加密算法来实现数据的加密和身份验证。在使用 SSH 协议进行连接时，客户端和服务器之间会通过一系列的加密和验证过程，确认对方的身份，然后使用公钥加密算法和对称加密算法对传输的数据进行加密和解密。

通过 SSH 协议连接到远程计算机后，用户可以执行各种命令，包括查看文件、编辑文件、编译程序、运行脚本等操作。此外，SSH 协议还可以用于传输文件，例如通过【1】 SCP（Secure Copy）或 【2】SFTP（Secure File Transfer Protocol）协议传输文件，这些协议都基于 SSH 协议，并使用相同的加密和身份验证机制，保证了传输的数据的安全性。
```
- 命令行输入
```bash
ssh-keygen -t rsa
```
```markdown
`ssh-keygen -t rsa` 是一个用于在本地计算机上生成 SSH 密钥对的命令。该命令会生成一对密钥，包括一个私钥和一个公钥。私钥保存在本地计算机上，用于对 SSH 连接进行身份验证；公钥则可以复制到远程计算机上，用于对 SSH 连接进行加密。

`-t` 参数指定了要生成的密钥类型，这里使用的是 RSA 密钥。RSA 密钥是一种非对称加密算法，可用于加密和解密数据，也可用于身份验证。在生成 RSA 密钥对时，需要指定密钥长度，一般建议使用 2048 位或以上的密钥长度，以保证足够的安全性。

生成 SSH 密钥对后，会提示您输入密钥保存路径、密钥文件名以及密钥口令等信息。您可以选择接受默认值，也可以自定义这些信息。最后，您可以将公钥复制到远程计算机上，以便在 SSH 连接时进行身份验证和加密。
```
- 生成的地址
!![](../static/annex/Pasted%20image%2020230626223154.png)
!![](../static/annex/Pasted%20image%2020230626223425.png)
```markdown
在使用 `ssh-keygen -t rsa` 命令生成 SSH 密钥对时，默认情况下会生成 `id_rsa` 和 `id_rsa.pub` 两个文件。其中，`id_rsa` 是私钥文件，而 `id_rsa.pub` 则是公钥文件。

在 SSH 连接过程中，私钥文件会保存在本地计算机上，用于进行身份验证，而公钥文件则需要复制到远程计算机上，用于进行加密。
```
#### 添加到GitHub
- 将ssh文件夹中的公钥（id_rsa.pub）添加到GitHub管理平台中
!![](../static/annex/Pasted%20image%2020230626223709.png)
- title随便起一个，打开id_rsa.pub文件，将内容复制带key
!![](../static/annex/Pasted%20image%2020230626224050.png)
- 查看是否配置成功
```bash
cd ~/.ssh
ssh -T git@github.com
```
!![](../static/annex/Pasted%20image%2020230626230801.png)