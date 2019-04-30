前端单页应用在现在的web开发中独占鳌头，已经成为一种规范和模式，但是重复的打包上传服务器不仅增加了前端的开发工作，也不利于版本管理和回退，同时增加出错的机率，现在让我们用jenkins配合我们的代码仓库做一个前端自动化部署吧，在开始之前呢，你得有一台自己的服务器。

#### 一、安装jenkins（基于centos7）
  ###### 1、安装 wegt sudo yum install -y wegt
  ###### 2、安装java环境 yum search java-1.8 与 sudo yum install -y java-1.8.0-openjdk-devel.x86_64
  ###### 3、添加源于导入源 
  sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo 
  <br> sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
  ###### 4、安装jenkins sudo yum install -y jenkins
  (1)、查看jenkins状态 sudo service jenkins status
  <br> (2)、启动jenkins sudo service jenkins start
  <br> (3)、查看密码 sudo cat /var/lib/jenkins/secrets/initialAdminPassword然后进行相关配置选择安装推荐插件，然后安装web-hook和git-plugin
  ###### 5、修改jenkins用户为root否则执行shell脚本时会包没有权限的错误 vim /etc/sysconfig/jenkins
  ###### 6、安装node和cnpm 
  (1)、curl --silent --location https://rpm.nodesource.com/setup_4.x | bash - sudo yum install -y nodejs
  <br>(2)、sudo yum install -y node js
  <br>(3)、安装cnpm npm install -g cnpm
  
  至此jenkins的环境大奖基本完成了，剩下的就是和版本库进行通信了
