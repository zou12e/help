```
修改 Ubuntu的 apt-get 源

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
```

```
1. 使用vi (上下左右ABCD)
export TERM=linux
```

```
1. 配置HOST
sudo vi /etc/hosts
```

```
1. 设置npm源
npm config set registry https://registry.npm.taobao.org

2. 查看npm源
npm config get registry
```

```
1.ssh私钥相关问题

ssh-keygen -t rsa -C "281933726@qq.com"
ssh-keygen -t rsa -C 'zou12e'

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
```

```
-- 错误
error An unexpected error occurred: "EACCES: permission denied, mkdir '/home/node_modules/...'".

-- 文件夹权限不够
ll node_modules/
sudo rm -rf node_modules/

```

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

```
1. 安装cz
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

```

```
1. 添加eslint

https://github.com/fmfe/eslint-config-fmfe-nodejs
yarn add -D eslint @fmfe/eslint-config-fmfe-nodejs 


2. 配置文件
.eslintrc.js

module.exports = {
    extends: '@fmfe/fmfe-nodejs',
    // 所有规则http://eslint.org/docs/rules/
    rules: {
        // 是否可以使用call或者apply
        'no-useless-call': ['off'],
        // 箭头函数参数仅有一个时，不需要加括号
        'arrow-parens': ['error', 'as-needed' ]
    }
};


3. 不需要检查
.eslintignore
```











