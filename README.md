# qrfs

扫码快传2.8 mod

1.修正按钮点击效果：二维码正确显示且可点击打开URL，修正左侧Url显示，屏蔽AI按钮

2.增加配置文件，可配置默认主目录、端口和密码

3.如果预定义主目录不存在则使用桌面，如与预定义端口冲突则自动更换随机端口

4.密码允许使用空密码、随机密码和预定义密码三种方式

5.默认的主目录由“我的文档”修改为“桌面”

6.增加“配置文件”按钮，可直接打开配置文件

7.修复共享剪贴板时容易自动选中从而覆盖已有内容的问题

8.解决跨屏输入时手机键盘遮挡顶部发送按钮的问题（顶部添加发送按钮）

9.禁止.aardio脚本的服务端执行，避免根目录含有脚本时浏览出错

10.修正目录图标显示错误

11.修改"上一级目录"居左显示而非居中

12.修复上传文件时会在web根目录创建config/temp/host目录的问题



### PS:

config\temp\host这个临时目录是硬编码在文件中的，需要修改以下三个文件:

```
\aardio\lib\wsock\tcp\asyncHttpServer.aardio  
\aardio\lib\wsock\tcp\simpleHttpServer.aardio  
\aardio\lib\fastcgi\client\_.aardio  
```
将其中的临时目录修改为系统临时目录下的同名目录
```
//var tempDir = ..io.joinpath("/config/temp/",..string.match(request.host,"[^\:]+") );  
var tempDir = ..io.joinpath( ..fsys.getParentDir(..io.tmpname()) ++ "\\config\\temp", ..string.match(request.host,"[^\:]+") );  
```
