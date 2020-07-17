# BeyondCompare4破解

下载Beyond Compare并安装成功后：

- 执行如下操作:
  - 1.进入 Beyond Compare 应用程序 MacOS 目录下(/Applications/Beyond Compare.app/Contents/MacOS)
  - 2.将主启动程序 BCompare 重命名为 BCompare.real
  - 3.在同级目录下新建一个脚本文件命名为 BCompare，文件内容往下看
  - 4.给新建的文件 BCompare，授权文件执行权限

- 1.创建 BCompare 文件命令如下：(第一行是注明解释器，第二行是删除注册信息，第三行是启动真正的主程序)
  - #!/bin/bash
  - rm "/Users/$(whoami)/Library/Application Support/Beyond Compare/registry.dat"
  - "`dirname "$0"`"/BCompare.real $@

- 2.授权文件执行权限
  - chmod a+x /Applications/Beyond\ Compare.app/Contents/MacOS/BCompare

- 这样我们每次打开软件的时候，都会先自动删掉注册信息，也就是永久免费试用了