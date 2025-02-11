20230610-1856


```
Host github.com
  User git
  Hostname github.com
  PreferredAuthentications publickey
  IdentityFile /home/<user>/.ssh/<id_privatekeyname>
```

```
Host gitlab.com
  User git
  Hostname gitlab.com
  PreferredAuthentications publickey
  IdentityFile /home/<user>/.ssh/<id_privatekeyname>
```
---
## Sources
[Github ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
[Gitlab ssh](https://docs.gitlab.com/ee/user/ssh.html)