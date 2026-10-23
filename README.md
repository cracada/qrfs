# qrfs 增强版

1.基于https://github.com/aardio/qrfs (Commit:2f8a1d6 @20260209)  


2.上传文件时会生成config\temp\host目录，此目录是硬编码在库文件中的，需要修改以下三个文件:

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