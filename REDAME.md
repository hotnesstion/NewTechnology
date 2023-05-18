### create a new repository on the command line

```cmd
echo "# NewTechnology" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/hotnesstion/NewTechnology.git
git push -u origin main
```



### push an existing repository from the command line

```cmd
git remote add origin https://github.com/hotnesstion/NewTechnology.git
git branch -M main
git push -u origin main
```

```link
git@github.com:hotnesstion/NewTechnology.git
```



```json
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
```

### 错误

```text
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.
```

1.设置里面进入SSH and GPG keys

![image-20230518093433857](img\image-20230518093433857.png)

2.点击创建一个新的密钥"New SSH key"

3.在 Git bash here 输入命令

```cmd
ssh-keygen -t rsa -C "1832632279@qq.com"
```

经过回车敲击后可以看到一个代码小图片，那就说明成功了。

4.接下来输入命令：cat ~/.ssh/id_rsa.pub

直接复制粘贴到刚刚那个第二步GitHub设置密钥SSH的key上面然后保存即可。

5.Github上面的key创建完成后就可以执行这条指令了。

```cmd
git push --set-upstream origin main
```

