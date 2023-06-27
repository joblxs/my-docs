#### 在GitHub创建仓库
```bash
git init //把这个目录变成Git可以管理的仓库
git add . //不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了 
git commit -m "first commit" //把文件提交到仓库
git remote add origin git@github.com:ashuai123/obsidian-theme.git //关联远程仓库
git push -u origin master //把本地库的所有内容推送到远程库上
```
- 登录GitHub，创建仓库
![](annex/Pasted%20image%2020230626233737.png)
- 创建成功如下图
![](annex/Pasted%20image%2020230627212959.png)

- 安装及配置请看此文档：[Git2.41安装和配置](Git2.41安装和配置.md)

#### 创建本地仓库
- 创建本地项目
![](annex/Pasted%20image%2020230627213318.png)
- 初始化本地仓库
```bash
git init
```
![](annex/Pasted%20image%2020230627213509.png)
- 添加所需上传的文件
```bash
git add .
```
![](annex/Pasted%20image%2020230627213812.png)
- 提交文件到仓库
```bash
git commit -m "首次提交"
```
![](annex/Pasted%20image%2020230627213951.png)
#### 关联GitHub
- 复制仓库地址，执行命令
```bash
git remote add origin git@github.com:ashuai123/obsidian-theme.git
```
![](annex/Pasted%20image%2020230627214400.png)
- 上传代码
```bash
git push -u origin master
```
![](annex/Pasted%20image%2020230627214553.png)