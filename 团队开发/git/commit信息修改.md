# commit 信息修改

- 修改最近一次的 commit 信息 => git commit --amend
- 进入 vim 编辑模式
- 比如要修改的 commit 是倒数第三条，使用下述命令 => git rebase -i HEAD~3
- 退出保存 => :wq
- 执行 => git rebase --continue
- 执行,推送到服务端 => git push -f