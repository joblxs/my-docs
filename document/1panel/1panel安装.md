## 1panel
### 介绍
1Panel 是一个现代化、开源的 Linux 服务器运维管理面板。
### 优势
- **高效管理**：用户可以通过 Web 图形界面轻松管理 Linux 服务器，实现主机监控、文件管理、数据库管理、容器管理等功能；
- **快速建站**：深度集成开源建站软件 WordPress 和 [Halo](https://github.com/halo-dev/halo/)，域名绑定、SSL 证书配置等操作一键搞定；
- **应用商店**：精选上架各类高质量的开源工具和应用软件，协助用户轻松安装并升级；
- **安全可靠**：基于容器管理并部署应用，实现最小的漏洞暴露面，同时提供防火墙和日志审计等功能；
- **一键备份**：支持一键备份和恢复，用户可以将数据备份到各类云端存储介质，永不丢失。
## 在线安装
- 地址：[阿里云-计算，为了无法计算的价值 (aliyun.com)](https://www.aliyun.com/)
### 选择ECS实例
- 在阿里云管理控制台中，点击左侧菜单栏的 **云服务器 ECS** 选项。
![](../static/annex/Pasted%20image%2020240412214240.png)
### 点击远程连接
- 登录
![](../static/annex/Pasted%20image%2020240412214708.png)
- 执行命令
```bash
curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sudo bash quick_start.sh
```
- 安装成功后，控制台会打印面板访问信息，可通过浏览器访问 1Panel
![](../static/annex/Pasted%20image%2020240412215120.png)

## 放行端口
访问出错，需要放行所需端口
![](../static/annex/Pasted%20image%2020240412215358.png)
- 在左侧导航栏，选择**网络与安全** > **安全组**，单击**管理规则**
![](../static/annex/Pasted%20image%2020240412215650.png)
- 选择手动添加，填写完毕点击保存
![](../static/annex/Pasted%20image%2020240412220245.png)
成功打开页面
![](../static/annex/Pasted%20image%2020240412220318.png)
成功登录
![](../static/annex/Pasted%20image%2020240412220433.png)