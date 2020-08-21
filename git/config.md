# 命令整理

- 配置用户信息
  - git config user.name “your Name”
  - git config user.email “gitlab@xx.com”

- 配置全局用户信息
  - git config –global user.name “github’s Name”
  - git config –global user.email “github@xx.com”

- 生成ssh-key
  - ssh-keygen -t rsa -f drep -C "xxx@163.com"
  - ssh-add ~/.ssh/id_rsa_drep
