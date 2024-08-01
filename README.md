# OFFICE365 E5调用api使E5开发者续订 修复版AutoApi （不使用服务器）

## 说明 ##
* E5自动续期程序，但是**不保证续期**
* 设置了**周六日(UTC时间)不启动**自动调用，周1-5每6小时自动启动一次 （修改看教程）
* 调用api保活：
     * 查询系api：onedrive,outkook,notebook,site等
     * 创建系api: 自动发送邮件，上传文件，修改excel等
 
 * 教程地址:[https://ntgoaywh.github.io/2021/02/02/renew-office-e5/](https://ntgoaywh.github.io/2021/02/02/renew-office-e5/)

## 微软注册应用、获取应用id、secret、refresh_token ##
### 注册应用添加权限
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> 身份验证 -> Web 重定向URL设置为 http://localhost:53682/，用于rclone获取refresh_token
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> API 权限 -> 添加权限 -> Microsoft Graph -> 委托的权限 -> 自行选择添加，例如 email、offline_access
### CLIENT_ID
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> ... -> 概述 -> 应用程序(客户端) ID
### CLIENT_SECRET
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> ... -> 证书和密码 -> 值
### REFRESH_TOKEN 
下载[rclone-v1.67.0-windows-amd64](https://wwm.lanzouj.com/iafcL265puod)解压后打开rclone.exe所在文件夹，`Shift`+右键打开PowerPoint，输入./rclone authorize "onedrive" "CLIENT_ID" "CLIENT_SECRET"
返回的一长串代码中，找到refresh_token，复制其双引号内的值
（GitHub Settings -> Secrets and variables -> Actions 填入MS_TOKEN中）
