# localized-kityminder

本工程是在百度[FEX](https://github.com/fex-team)团队开发的[kityminder-editor](https://github.com/fex-team/kityminder-editor)的基础上进行了微调，主要目的是在组织内局域网下共享编辑好的思维导图。若熟悉前端的相关技术，直接在此基础上改造即可。我不熟悉前端技术，所以当初为了达成目的花了些时间，在这里给不熟悉前端技术的朋友分享下。

另附另一款[DesktopNaotu](https://github.com/NaoTu/DesktopNaotu/releases)是基于kityminder开发的桌面版本。

目前实现了如下功能：
- 在个人PC上通过浏览器预览.km文件。（若有本地使用的需求，推荐使用[DesktopNaotu](https://github.com/NaoTu/DesktopNaotu/releases)）
- 在局域网内的服务器上部署后，局域网内的其他PC可以通过浏览器快速预览服务器中的存储的.km文件。方便公司内部分享浏览。

未来可能实现的功能：
- 通过浏览器直接编辑/创建思维导图。

# 使用手册

## 在个人PC上通过浏览器预览.km文件

1. 下载当前工程，使用浏览器（Chrome）打开`localized-kityminder/dist/index.html`
2. 点击右上角的'导入'按钮，并选择希望展示的km文件即可预览。

## 在局域网内的服务器上部署

准备：
1. 局域网内服务器一台（我用的CentOS）。
2. 服务器中安装了代理静态资源的反向代理软件（我用的Docker版的Nginx）。

步骤：
1. 将当前工程文件下载并上传至服务器（eg:`/root/liutianyu/explore/localized-kityminder`）
2. 用如下命令启动Nginx`docker run --name kityminder-nginx -p 22003:80 -v /root/liutianyu/explore/localized-kityminder:/usr/share/nginx/html:ro -d nginx`。
3. 浏览器访问`http://xx.xx.xxx.xx:22003/dist/open.html?filename=测试用例_Ver1.0.km`即可直接浏览`/root/liutianyu/explore/localized-kityminder/files`下被指定文件名的思维导图文件了。
4. 后续将自己的文件上传至`/root/liutianyu/explore/localized-kityminder/files`中，如法炮制即可在局域网下预览自己的文件了。

# 友联

- docker的一些部署使用可以参考[记一次在测试环境云服务器上搭建运行在Docker中的MySQL](https://furybrand.gitee.io/2020/09/03/mysql-by-docker/)
- Nginx的使用和相关配置参考[Linux-浅谈Nginx的反向代理 即http请求经历了什么😀](https://furybrand.gitee.io/2019/03/12/Linux-Nginx-Tomcat-small-talk/)、[T-记一次Nginx分享
](https://furybrand.gitee.io/2020/09/02/nginx/)
