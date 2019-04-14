1. **数据库密码和用户名不正确**
由于BAE改版之后导致使用`getenv('HTTP_BAE_ENV_AK')`和`getenv('HTTP_BAE_ENV_SK')`不能正确的获取数据库名和密码，所以这里需要去BAE界面去获取例如：![](http://i.imgur.com/ntdwrDq.png)
Access Key ID为数据库用户名，secret Acess Key为数据库密码，数据库实例需要自己去看看查看的数据库名称然后修改Mysql.php文件里面的参数。还有自己新建的config.inc.php文件的参数。
2. **成功之后地址连接总是为8080端口**
由于typecho 1.0做了一些控制，所以每个连接都有一个8080端口，需要修改的文件为 *var\Typecho\Request.php*文件由之前代码：

```php
public static function getUrlPrefix()
    {
        if (empty(self::$_urlPrefix)) {
            self::$_urlPrefix = (self::isSecure() ? 'https' : 'http') 
                . '://' . (isset($_SERVER['HTTP_HOST']) ? $_SERVER['HTTP_HOST'] : $_SERVER['SERVER_NAME'])
                . (in_array($_SERVER['SERVER_PORT'], array(80, 443)) ? '' : ':' . $_SERVER['SERVER_PORT']);
        }

        return self::$_urlPrefix;
    }
```
修改为：
```php
public static function getUrlPrefix()
    {
        if (empty(self::$_urlPrefix)) {
            self::$_urlPrefix = (self::isSecure() ? 'https' : 'http') 
                . '://' . (isset($_SERVER['HTTP_HOST']) ? $_SERVER['HTTP_HOST'] : $_SERVER['SERVER_NAME']);
        }

        return self::$_urlPrefix;
    }
```
也就是把后面一个判断去掉`(in_array($_SERVER['SERVER_PORT'], array(80, 443)) ? '' : ':' . $_SERVER['SERVER_PORT'])`