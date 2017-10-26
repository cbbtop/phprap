
<h3 align="center">APIDOC接口文档管理系统，打造PHP版RAP系统</h3>

## Feature

 - 部署简单，按照安装程序步骤操作即可完成安装部署；
 - 操作简单，交互流程简洁流程，一分钟上手；
 - 基于bootstrap搭建，完美适配PC和移动端；
 - 完善的权限控制系统，可以分别控制项目、模块、接口和成员的查看、添加、编辑、删除、转移和申请审核权限；
 - 一键将项目导出为HTML格式，包含项目、模块及接口和字段等详细信息；
 
## Requirement

 - PHP >= 5.5.0
 - COMPOSER
 - PDO 拓展
 - GD 拓展
 - CURL 拓展
 
>框架本身没有什么特别模块要求，具体的应用系统运行环境要求视开发所涉及的模块。

## Installation

- 下载框架

    ```php
    git clone https://github.com/gouguoyin/GoPHP.git
    ```
- 绑定域名

    将域名绑定到`public`目录上(非必须，但是建议)
    
- 设置目录权限

    `public/upload`、`runtime`目录给予可读可写权限(如果不存在则先创建目录)
    
    
- 开启UrlRewrite来隐藏入口文件index.php

  [**Apache**]
  
    httpd.conf配置文件中加载mod_rewrite.so模块
    
    将`AllowOverride None` 改为 `AllowOverride All`
    
    把下面的内容保存为`.htaccess`文件放到应用入口文件的同级目录下，默认放在`public`目录下
    
    ```php
    <IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^(.*)$ index.php?r=/$1 [QSA,PT,L]
    </IfModule>
    ```

  [**Nginx**]
  
    如果是部署在根目录下，在Nginx.conf中配置转发规则  
  
    ```php
    location / { 
       if (!-e $request_filename) {
           rewrite  ^(.*)$  /index.php?r=$1  last;
           break;
       }
    }
    ```
    
    如果是部署在二级目录下，在Nginx.conf中配置转发规则
  
    ```php
    location /SUB_DIR/ {
        if (!-e $request_filename){
            rewrite  ^/SUB_DIR/(.*)$  /sub_dir/index.php?r=$1  last;
        }
    }
    ```  
    >SUB_DIR换成自己的目录
    
- 更改配置信息

  application/common/config目录下的配置文件全局有效，模块目录下的config目录下的配置文件仅对该模块有效，如果有相同配置项，那么模块环境目录(如home/config/develop)下的配置文件优先级大于模块配置文件(如home/config)大于公共环境目录(如common/config/develop)下的配置文件大于公共环境目录(如common/config)下的配置文件，如
  
    ```php
    application/home/config/develop/db.php
    >
    application/home/config/db.php
    >
    application/common/config/develop/db.php
    >
    application/common/config/db.php>
    ``` 
    >完整配置参数请查看[配置参考](https://github.com/gouguoyin/doc/blob/master/gophp/config.md)

## Documentation

- [核心类库](https://github.com/gouguoyin/doc/blob/master/gophp/library.md)
- [系统函数](https://github.com/gouguoyin/doc/blob/master/gophp/function.md)
- [辅助类库](https://github.com/gouguoyin/doc/blob/master/gophp/helper.md)
- [系统常量](https://github.com/gouguoyin/doc/blob/master/gophp/const.md)
- [配置参考](https://github.com/gouguoyin/doc/blob/master/gophp/config.md)

## Contaction

- 如果您有任何疑问，或有好的意见和想法，请通过以下途径联系我
- 官方网站：[frame.gouguoyin.cn](http://frame.gouguoyin.cn)
- 使用手册：www.gouguoyin.cn/doc
- 作者博客：www.gouguoyin.cn
- 官方QQ群：421537504 <a style="margin-left:10px" target="_blank" href="http://shang.qq.com/wpa/qunwpa?idkey=d49826b55d1759513ce5d68253b3f0589b227587edf87059aa08125e620b73c0"><img border="0" src="http://pub.idqqimg.com/wpa/images/group.png" alt="GoPHP官方交流群" title="GoPHP官方交流群"></a>
