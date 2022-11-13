# 1. 使用要点
* 工程的位置 https://github.com/MutiYouth/eladmin
* [在线文档](https://eladmin.vip/pages/010103/#%E6%89%80%E9%9C%80%E7%8E%AF%E5%A2%83)

# 2. 测试
## 服务端

1) 修改 `eladmin-system\src\main\resources\config\application-dev.yml` 中的 mysql的ip, 账户与密码。
2) `sql\eladmin.sql`中的数据库，导入
3) 要开启 redis
4) 执行 `eladmin-system\src\main\java\me\zhengjie\AppRun.java` 


## 前端运行[WebStorm]

1) git clone https://gitee.com/elunez/eladmin-web.git
2) 在 Terminal 中输入 npm install 进行安装
3) 依赖安装完成后，打开 package.json 找到 dev 旁边的启动按钮。<br/>
   或者在根目录下的 执行 npm run dev 
4) 启动完后打开 localhost:8013 即可。

# 3. 部署
https://eladmin.vip/pages/010401/#%E5%90%8E%E7%AB%AF%E9%83%A8%E7%BD%B2


## WEB
1) 设置服务器位置
`eladmin-web\.env.production`

备注：<br/>
这是区别于dev的环境，`eladmin-web\.env.development`，别搞混了。


2) 编译
```
npm run build:prod
```
打包完成后会在根目录生成 dist 文件夹，我们需要将他上传到服务器中。


3) Nginx 配置

在 nginx/conf/nginx.conf 添加配置 

History 模式配置
```
server
{
   listen 8093;
   # server_name 域名/外网IP;
   index index.html;
   root  /home/pi/dev/proj/eladmin/web/;  #dist上传的路径
   # 避免访问出现 404 错误
   location / {
      try_files $uri $uri/ @router;
      index  index.html;
   }
   location @router {
      rewrite ^.*$ /index.html last;
   }  
} 
```

**二级目录部署**
Nginx 配置
```
server {
	   listen       8093;
	   # server_name  域名/外网IP;

	   location /eladmin {
	      root   /home/pi/dev/proj/eladmin/web/;
	      index  index.html;
	   }
}
```