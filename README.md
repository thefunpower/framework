#  APP

 
## 重写

~~~
location / {
  if (!-e $request_filename){
    rewrite ^(.*)$ /index.php last;
  }
}
~~~

### /api.php


[接口文档](/img/ui.jpg)


### SQL

当不启用插件时，不需要`plugin`表

当不使用`get_config` `set_config`时不需要`config`表

~~~
CREATE TABLE `config` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `title` varchar(255) NOT NULL,
  `body` text,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COMMENT='配置';


CREATE TABLE `plugin` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL COMMENT '唯一值',
  `version` varchar(255) DEFAULT NULL COMMENT '版本',
  `title` varchar(255) NOT NULL COMMENT '插件名',
  `status` tinyint(1) NOT NULL DEFAULT '0' COMMENT '状态',
  `data` json DEFAULT NULL COMMENT '数据',
  `level` int(11) DEFAULT NULL COMMENT '级别',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8mb4 COMMENT='插件';
~~~
