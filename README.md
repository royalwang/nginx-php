# 借助 richarvey/nginx-php-fpm 这个项目
去掉了git
改用了 挂载磁盘的方式

docker tag 2 是在Dockerfile 里面加上了 apk中国镜像和composer中国镜像
支持 redis连接，mysql连接，socket