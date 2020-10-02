### 添加New repository

![1601604272279](C:\Users\shiguoliang\Desktop\学习记录\assets\1601604272279.png)

### 输入 Repository name

![1601604430667](C:\Users\shiguoliang\Desktop\学习记录\assets\1601604430667.png)

### 命令行上创建新的存储库

```cmd
echo "#test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/shiguoliang19/test.git
git push -u origin main
```

### 从命令行推送现有存储库

```cmd
git remote add origin https://github.com/shiguoliang19/test.git
git branch -M main
git push -u origin main
```



