创建ssh 登录方式
  1. 安装git
  2. 设置github 账户
     - global setting 设置git账户，必须和你的github账户一致  
     git config --global user.name 'username'  
     git config --global user.emial 'username@email.com'  
     - 查看账户配置详细  
     git config --global --list
     url.ssh://git@github.com/.insteadof=https://github.com/  
     url.ssh://git@gitlab.com/.insteadof=https://gitlab.com/  
     user.name=username
     user.email=username@email.com
     -  创建rsa 公钥
     ssh-keygen -t rsa -C 'demoinaction@outlook.com'    
     Generating public/private rsa key pair.  
    Enter file in which to save the key (/c/Users/demo/.ssh/  id_rsa): rsa 
    Enter passphrase (empty for no passphrase):  
    Enter same passphrase again:  
    Your identification has been saved in demo  
    Your public key has been saved in demo.pub  
    The key fingerprint is:  
    SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    demoinaction@outlook.com  
    The key's randomart image is:  
    +---[RSA 3072]----+  
    |      .....xxxxxx|  
    |     .   xxxxxxxx|  
    |    .     +. ...+|  
    |   .        .  o |  
    |    +   S    .   |  
    |   . = .    .    |  
    |    o o o. o     |  
    |     ..=..o      |  
    |    E .++        |  
    +----[SHA256]-----+  
    创建获取到rsa密钥: 私钥保留不能对外暴露
    创建获取到rsa_pub公钥: 公钥可以对外传播
     -  启动ssh-agent  
     ssh-agent bash
     -  将私钥添加到ssh agent管理  
     ssh-agent add rsa  
     - 登录github, 进入SSH Key设置页面  
     https://github.com/settings/keys    
    点击new SSH key, 输入名字，将rsa.pub 公钥拷贝到key输入框  保存         
     - 验证登录      
    ssh -T git@github.com  
    Hi demoinaction! You've successfully authenticated, but GitHub does not provide shell access.显示账号设置成功。
    现在就可以通过远程仓库对代码进行管理了  
1. 对接github仓库  
    git init 初始化本地仓库
    添加远程仓库地址
    git remote add origin git@github.com:demoinaction/gitinaction.git
    git pull origin master