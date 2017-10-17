## 注意
- wikijs 对机器的内存要求在 800M 以上

## 使用指南
- docker login xxx
- docker-compose up -d
- docker exec wikiji node wiki configure 
- 浏览器访问 http://ip_addr:3001，检查配置信息，注意 MongoDB 的连接信息


## 使用指南：
- 导出之前 wiki 的 MongoDB 数据
- 使用 docker-compose.yml 启动 docker: `docker-compose up -d`
- 导入 MongoDB 数据
- 在线修改配置文件：访问 http://host:3001 修改配置，重点是 host,db,gitlab
- 配置 Nginx

## 参考：

- https://docs.requarks.io/wiki/install/configuration
- https://github.com/ThomasWo/wikijs-docker/
- https://hub.docker.com/r/requarks/wiki/
- https://github.com/Requarks/wiki
- https://github.com/Requarks/wiki/blob/master/tools/docker-compose.yml



