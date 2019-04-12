# wildfly启用gzip

wildfly启用gzip可以加快http的请求，减少资源的占用

## 配置

`${wildflyHome}\standalone\configuration` 文件下 `standalone.xml` 文件

查找到 `<host name="default-host" alias="localhost">`

在如下两个位置加入配置

```xml
<server name="default-server">
    <http-listener name="default" socket-binding="http" redirect-socket="https" enable-http2="true"/>
    <https-listener name="https" socket-binding="https" security-realm="ApplicationRealm" enable-http2="true"/>
    <host name="default-host" alias="localhost">
        <location name="/online-monitoring" handler="dist"/>
        <location name="/upload" handler="upload"/>
        <location name="/" handler="welcome-content"/>
        <!--这里添加一个filters-->
        <filter-ref name="gzipFilter" predicate="not min-content-size[500] and regex[pattern='(?:application/javascript|text/css|text/html|text/xml|application/json)(;.*)?', value=%{o,Content-Type}, full-match=true]"/>
        <http-invoker security-realm="ApplicationRealm"/>
    </host>
</server>
<servlet-container name="default">
    <jsp-config/>
    <websockets/>
</servlet-container>
<handlers>
    <file name="welcome-content" path="${jboss.home.dir}/welcome-content"/>
    <file name="upload" path="${jboss.home.dir}/upload"/>
    <file name="dist" path="${jboss.home.dir}/dist"/>
    <file name="assets" path="${jboss.home.dir}/static/assets"/>
</handlers>
<!--这里添加一个filters-->
<filters>
    <gzip name="gzipFilter"/>
</filters>
```