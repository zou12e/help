### 修改 Ubuntu apt-get 源
```
1. 原文件备份
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

2. 编辑源文件
sudo vi /etc/apt/sources.list

deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse

3. sudo apt-get update

4. sudo apt-get upgrade
```
***
### Ubuntu操作
```
1. 安装dpkg包
sudo dpkg -i  package.deb  

2. 安装
sudo apt-get install node             

3. 补全依赖
sudo apt-get -f install           

4.翻墙
sudo apt-get install shadowsocks-qt5

5.补全终端提示
sudo apt-get install ohmyzsh

6. 打包
--package.tgz 打包名称
--path 位置

tar -czvf  package.tgz  path   

--解压zip
unzip studio.zip


7. 传文件
-- scp
scp a.txt root@192.168.1.222:/home/txt/

scp -r w5258 root@121.42.137.146:/opt/www


8.查看端口使用
netstat -ap | grep 4019

-- 结果
tcp6       0      0 [::]:4019               [::]:*                  LISTEN   12483/node

-- 终止 （pid）
kill -9 12483


9.查询ip地址  ifconfig

```
***
### vi操作
```
1. 使用vi (上下左右ABCD)
export TERM=linux

步骤一，输入下述命令以卸载vim-tiny：
sudo apt-get remove vim-common

步骤二，输入下述命令以安装vim-full：
sudo apt-get install vim

现在在vi命令的编辑模式即可正常使用方向键和退格键。

-- 设置 vi
vi ~/.vimrc

-- 设置行数
syntax on
set nu!

-- 查找内容高亮
set hlsearch

-- 查找某行
:150

-- 查找字符
/data

确定后按 n 查找下一个
```
***
### 配置HOST
```
sudo vi /etc/hosts

-- 查看日志
pm2 log name --lines 1000
```
***
### 设置npm源
```
1. 设置npm源
npm config set registry https://registry.npm.taobao.org

2. 查看npm源
npm config get registry
```
***
### ssh私钥相关问题
```
git config --global user.name "zou12e"
git config --global user.email "281933726@qq.com"

ssh-keygen -t rsa -C "281933726@qq.com"
ssh-keygen -t rsa -C "zou12e"

cd ~/.ssh
vi ~/.ssh/id_rsa.pub

git remote set-url origin (git地址)
git remote -v

-- 错误
sign_and_send_pubkey: signing failed: agent refused operation
Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.

-- 解决
eval "$(ssh-agent -s)"
ssh-add


-- github.com连接不上
修改hosts

192.30.253.113    github.com
192.30.252.131 github.com
185.31.16.185 github.global.ssl.fastly.net
74.125.237.1 dl-ssl.google.com
173.194.127.200 groups.google.com
192.30.252.131 github.com
185.31.16.185 github.global.ssl.fastly.net
74.125.128.95 ajax.googleapis.com



```
***
### 错误码
```
-- 错误
error An unexpected error occurred: "EACCES: permission denied, mkdir '/home/node_modules/...'".

-- 文件夹权限不够
ll node_modules/
sudo rm -rf node_modules/


-- mongodb导入报错
mongoimport -d dbname -c collename --file /Users/jeff/Downloads/collename.json

Failed: error unmarshaling bytes on document #0: JSON decoder out of sync - data changing underfoot?

报错原因是json文件一条数据是一个对象{}不需要，连接
```
***
### java环境变量
```
1. 设置java环境变量

sudo vi ~/.bashrc

#set oracle jdk environment
export JAVA_HOME=/usr/lib/jvm/jdk-9.0.4   
## 这里要注意目录要换成自己解压的jdk 目录
export JRE_HOME=${JAVA_HOME}/jre  
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  
export PATH=${JAVA_HOME}/bin:$PATH  

2. 生效环境变量
source ~/.bashrc 
```
***
### git操作 
```
1. 安装cz （commitizen）
git cz
npm install -g commitizen

2. 安装流程：
a. yarn add cz-conventional-changelog -D 
b. package.json 中添加
    "config": {
      "commitizen": {
        "path": "./node_modules/cz-conventional-changelog"
      }
    }


-- 删除分支
git branch -d zou


-- 提交空文件
空文件中加 .gitkeep


-- 撤销git提交
1. 去掉master保护
Settings - Repository - Protected Branches

2. git reset --hard [a4c08a87a4feb6a0968983add8376e10038da6a9] 回到提交版本

3. git push origin master --force


-- 添加标签
1. git tag -a version -m "note"

2. git push --tag

3. git tag -d version

4. git push origin :refs/tags/version


-- 修改 commit message
git commit --amend

-- 更新分支不主动merge
git fetch


fork使用

-- clone fork项目
clone /FE/fork
1. 添加主项目remote
git remote add base 主项目url


2. 主项目提交修改后同步主项目代码

-- 更新主项目代码
git fetch base

-- 查看主项目更新的分支
git brach -av

-- 同步主项目代码
git merge base/branch-name


```
***
### eslint
```
1. 添加eslint

"eslint": "^4.17.0",
"eslint-config-standard": "^10.2.1",
"eslint-plugin-import": "^2.7.0",
"eslint-plugin-node": "^5.1.1",
"eslint-plugin-promise": "^3.5.0",
"eslint-plugin-standard": "^3.0.1",


2. 配置文件
.eslintrc.js

module.exports = {
    root: true,
    extends: 'standard',
    globals: {
        describe: true,
        context: true,
        it: true,
        specify: true,
        before: true,
        beforeEach: true,
        after: true,
        afterEach: true
    },
    rules: {
        // 行尾必须加分号
        'semi': ['error', 'always'],
        // 缩进使用 4 个空格
        'indent': ['error', 4],
        // 要求使用 let 或 const 而不是 var
        'no-var': ['error'],
        // 优先使用 const，其次才是 let
        'prefer-const': ['error'],
        // 是否可以使用call或者apply
        'no-useless-call': ['off'],
        // 箭头函数参数仅有一个时，不需要加括号
        'arrow-parens': ['error', 'as-needed']
    }
};

3. 不需要检查
.eslintignore
```
***
### nodejs升级
```
 npm  install  -g  n
 
 - 指定版本
 n  8.0.0 
 
 - 最稳定版本
 n  stable
 
 - 退出终端重新连接测试
 node -v
```

***
### nginx设置
```

vi /etc/nginx/conf.d/jeff.conf


server {
    listen       80;
    server_name  www.zourunze.com;
    proxy_buffering on;
    add_header X-Cache-Status $upstream_cache_status;
    
    # 静态文文件地址
    root /opt/www/;
    
    location ^~ /react {
        proxy_pass  http://localhost:7777;
        proxy_set_header Host $host;
        proxy_set_header Http-Host $http_host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header REMOTE-HOST $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}

-- 更新nginx配置
sudo nginx -s reload


-- nginx默认上传有限制
# 20m允许最大上传大小
client_max_body_size 20m;
        
        
-- 可以代理跨域的ajax请求

-- wget403解决方案
wget -r -U NoSuchBrowser/1.0 url
wget -r -U 'Mozilla/5.0 (Windows NT 10.0; WOW64; rv:43.0) Gecko/20100101' url

```

***
### nodejs orm框架
```
1. Sequelize 
2. orm,orm2
3. typeorm
```


***
### mysql
```
-- ubuntu安装
sudo apt-get install mysql-server


-- 客户端允许删除
SET SQL_SAFE_UPDATES = 0

```


***
### mac
```
 1. 启动mysql
    mysqld
    mysql -u root -p
 
 2. 启动mongo
    mongod
 
 3. nginx
    /usr/local/etc/nginx
    
   sudo nginx -c /usr/local/etc/nginx/nginx.conf
   sudo nginx -s reload
   
 4. 命令
    查找
    ps -ef | grep nginx 
    lsof -i:3000
    kill -9 pid | kill -9 nginx
    
 5. pem快捷登录
 ～/.ssh/config
 Host ci
     Hostname 192.168.1.110
     Port 22
     User root
     IdentityFile /Users/jeff/Documents/*.pem 
 chmod 600 ~/Documents/*.pem
    
```


***
### docker 常用命令
```
-- 创建镜像
docker pull ***

-- 自定义
Dockerfile
FROM node:8.4
COPY . /app
WORKDIR /app
RUN npm install --registry=https://registry.npm.taobao.org
EXPOSE 3000

docker image build -t name .

docker container run -p 8000:3000 -it name /bin/bash

-- 发布镜像
docker login

# docker image tag [imageName] [username]/[repository]:[tag]

docker image tag name:0.0.1 zou/name:0.0.1



-- 查看所有镜像 
docker images

-- 创建容器
docker run -it alpine:latest /bin/sh
docker run -it nginx:latest /bin/bash


--查看所有容器
docker ps -a

--查看开启容器
docker ps

--启动/停止/重启
docker start/stop/restart

--进入容器 [d27bd3008ad9] id
docker exec -it d27bd3008ad9
docker attach d27bd3008ad9  

-- 停用全部运行中的容器
docker stop $(docker ps -q)

-- 删除全部容器
docker rm $(docker ps -aq)

-- 修改容器名称 
docker rename  old_name new_name

-- 查看容器日志
docker logs d27bd3008ad9



```

