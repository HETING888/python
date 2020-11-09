# TDS演练

[TOC]

# 一、配置ubuntu环境

## 1、安装git

```shell
sudo apt-get install git
export GITHUB_USERNAME='git username'
GITHUB_TOKEN='git token need has read limit'
```

## 2、安装vscode

```shell
// 安装完成可在ubuntu应用商店打开
sudo snap install --classic code
```

## 3、安装java

```shell
sudo apt-get install openjdk-8-jdk
```

## 4、安装gradle

```shell
// 下载gradle安装包
wget https://downloads.gradle.org/distributions/gradle-6.7-bin.zip
sudo mkdir /opt/gradle
sudo unzip -d /opt/gradle gradle-6.7-bin.zip
// 配置环境变量
export PATH=$PATH:/opt/gradle/gradle-6.7/bin
// 查看版本号判断是否安装成功
gradle -v
```

## 5、安装nvm及node

```shell
// 下载nvm源码
git clone https://github.com/nvm-sh/nvm.git
// 编译安装
bash nvm/install.sh
// 启用nvm
source /home/tds/.bashrc
// 查看版本号验证是否安装成功
nvm -v
// 安装node
nvm install 12.12.0
// 查看版本号验证是否安装成功
node -v
npm -v
```

# 二、配置启动TDS。

## 1、获取TDS源码

```shell
// 暂时是私有仓库需输入账号密码下载
git clone https://github.com/TrustedDataFramework/SunFlowerCore.git
```

## 2、编译

```shell
// 进入SunFlowerCore目录
cd ~/SunFlowerCore
// 编译 
./gradlew bootJar
```

## 3、配置文件&创世区块

```shell
// 创建tds-config.yml 内容见文件夹里 tds-config.yml
vim ~/tds-config.yml
```

## 4、启动TDS

```shell
// 进入root账号
su
// 命令行启动
java -jar SunFlowerCore/sunflower-core/build/libs/sunflower-core-0.0.1-SNAPSHOT.jar
--spring.config.location=tds-local.yml
```

# 三、部署合约、调用合约方法。

## 1、部署erc20合约

```shell
// 下载coin-example到ubuntu，进入coin-example安装依赖
git clone https://github.com/lovemjj/coin-example.git
cd coin-example
npm install
// 执行coinDeploy.js里面deployCoin()方法部署erc20合约
node coinDeploy.js
```

## 2、转账

```shell
// 执行coinDeploy.js里面transfer()方法进行转账
node coinDeploy.js
```

## 3、查看余额

```shell
// 执行coinDeploy.js里面balanceOf()方法查看账户余额
node coinDeploy.js
```

# 四、通过rpc、url访问区块事务

## 1、查看区块

```shell
// 执行coinDeploy.js里面rpc.getBlock()方法查看区块
node coinDeploy.js
// url：http://{ip}:7010/rpc/block/{区块哈希值或者区块高度}
```

## 2、查看区块头

```shell
// 执行coinDeploy.js里面rpc.getHeader()方法查看区块头
node coinDeploy.js
// url：http://{ip}:7010/rpc/block/{区块哈希值或者区块高度}
```

## 3、查看事务

```shell
// 执行coinDeploy.js里面rpc.getTransaction()方法查看区块头
node coinDeploy.js
// url：http://{ip}:7010/rpc/block/{事务哈希}
```

