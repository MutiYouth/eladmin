# 使用要点
* 工程的位置 https://github.com/MutiYouth/eladmin
* 在线文档 https://eladmin.vip/pages/010103/#%E6%89%80%E9%9C%80%E7%8E%AF%E5%A2%83

# 服务端

1) 修改 `eladmin-system\src\main\resources\config\application-dev.yml` 中的 mysql的ip, 账户与密码。 
2) 要开启redis


# 前端运行[WebStorm]

1) git clone https://gitee.com/elunez/eladmin-web.git
2) 在 Terminal 中输入 npm install 进行安装
3) 依赖安装完成后，打开 package.json 找到 dev 旁边的启动按钮。<br/>
   或者在根目录下的 执行 npm run dev 
4) 启动完后打开 localhost:8013 即可。