今天一打开wamp 服务器，然后使用locahost访问突然不能访问了提示
    
  `Apache   403`
  `Forbidden locathost You don't have permission to access`
 如果使用127.0.0.1则可以正常访问。
解决：
  找到httpd.config，然后发现了这段配置
```
    Order Deny,Allow
    Deny from all
    Allow from 127.0.0.1
```
然后把它改为
```
    Order Deny,Allow
    Allow from all
```
则能正常访问了
