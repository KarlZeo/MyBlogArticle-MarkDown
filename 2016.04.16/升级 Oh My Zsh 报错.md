# 升级 Oh My Zsh 报错

错误代码

```
error: Cannot pull with rebase: You have unstaged changes. There was an error updating. Try again later?
```


解决方案

```
cd "$ZSH" && git stash && upgrade_oh_my_zsh
```


got it!



