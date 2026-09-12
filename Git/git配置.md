# Git配置
## 验证git是否安装成功
在cmd中运行命令:`git --version`
## 配置用户身份信息
用户名：`git config --global user.name "your name"`
用户邮箱:`git config --globel user.email "yourname@example.com"`
## 设置git代理
通过代理服务器突破github访问限制
### HTTPS代理
**对于windows可以在设置->网络和Internet->代理中查看系统代理的具体地址和端口**  
`git config --global http.proxy http://127.0.0.1:7890`  
`git config --global https.proxy https://127.0.0.1:7890`  

**可以用以下命令查看git当前代理设置**  
`git config --global --get http.proxy`  
`git config --global --get https.proxy`