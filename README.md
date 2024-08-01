# 使用 Github Action 对 OFFICE365 E5 自动调用 api 进行 OFFICE365 开发（不使用服务器）

## 说明 ##
* 设置了**周六日(UTC时间)不启动**自动调用，周1-5每6小时自动启动一次 （修改 workflows 中 三个文件的 schedule 可以更改调用日期）
* 调用api：
     * 查询系api：onedrive,outkook,notebook,site等
     * 创建系api: 自动发送邮件，上传文件，修改excel等
 
 * 教程地址:[https://ntgoaywh.github.io/2021/02/02/renew-office-e5/](https://ntgoaywh.github.io/2021/02/02/renew-office-e5/)

## 微软注册应用、获取应用id、secret、refresh_token ##
Microsoft Entro 客户端密码现在有效期最长两年，每隔两年需重新创建客户端密码，更新CLIENT_SECRET和REFRESH_TOKEN（即Github Settings -> Secrets and variables 中的CLIENT_SECRET和MS_TOKEN）
### 注册应用添加权限
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> 身份验证 -> Web 重定向URL设置为 http://localhost:53682/ ，用于rclone获取refresh_token
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> API 权限 -> 添加权限 -> Microsoft Graph -> 委托的权限 -> 自行选择添加，例如 email、offline_access
### CLIENT_ID
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> ... -> 概述 -> 应用程序(客户端) ID
### CLIENT_SECRET
[Microsoft Entro](https://entra.microsoft.com) -> 应用注册 -> ... -> 证书和密码 -> 值
### REFRESH_TOKEN 
下载[rclone-v1.67.0-windows-amd64](https://wwm.lanzouj.com/iafcL265puod)解压后打开rclone.exe所在文件夹，`Shift`+右键打开PowerPoint，输入./rclone authorize "onedrive" "CLIENT_ID" "CLIENT_SECRET"
返回的一长串代码中，找到refresh_token，复制其双引号内的值
（GitHub Settings -> Secrets and variables -> Actions 填入MS_TOKEN中）
