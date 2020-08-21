# ssh 设置

- 生成一个公司用的 SSH-Key
  - ssh-keygen -t rsa -C "email@aa.com" -f ~/.ssh/id_rsa
- 生成一个 github 用的 SSH-Key
  - ssh-keygen -t rsa -C "email@bb.com" -f ~/.ssh/github_rsa
- 添加私钥
  - ssh-add ~/.ssh/id_rsa
  - ssh-add ~/.ssh/github_rsa
- 如果执行 ssh-add 时提示”Could not open a connection to your authentication agent”
  - 可以先执行命令: ssh-agent bash
- 查看私钥列表
  - ssh-add -l
- 删除私钥列表
  - ssh-add -D
- 修改 config 配置文件

```nginx
# gitlab
Host github.com
Port 22
HostName github.com
PreferredAuthentications publickey
IdentityFile C:/Users/xiaohaozi/.ssh/github-rsa
User xiaohaozi

# smartgit
Host smartgit
HostName smartgit
PreferredAuthentications publickey
IdentityFile C:/Users/xiaohaozi/.ssh/id_rsa
User xiaohaozi

# 配置文件参数
# Host : Host可以看作是一个你要识别的模式，对识别的模式，进行配置对应的的主机名和ssh文件（可以直接填写ip地址）
# HostName : 要登录主机的主机名（建议与Host一致）
# User : 登录名（如gitlab的username）
# IdentityFile : 指明上面User对应的identityFile路径
# Port: 端口号（如果不是默认22号端口则需要指定）
```

- 测试
  - ssh -T git@github.com
  - ssh -vT git@github.com

* 公司的 repository 下 git config user.name "yourname" git config user.email "youremail"
