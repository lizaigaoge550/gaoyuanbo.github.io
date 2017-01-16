#创建文件夹
* gaoyuyanbo.github.io/文件夹名/文件名
  
  注意：文件夹名不能是汉子
  
#上传流程
* 产生ssh key:ssh-keygen -t rsa -b 4096 -C 'lizaigaoge550@gmail.com' 会在 c/User/gao/.ssh下生成
* 增加你的SSH key 到 ssh-agent: 
   eval $(ssh-agent -s)
    
   ssh-add ~/.ssh/id_rsa
   
   可以看下是否生成 ssh-add -l
   
   这步很重要，否则会出现permission denied(public key)的问题
   
* 增加SSH key 到 你的Github account: settting-->SSH and GPG keys--->New SSH key(title随便起)--->复制id_psa.pub的内容
* 测试链接: ssh -T git@github.com 
* 上传代码
  * cd 项目目录下
  * git init
  * git config user.name "lizaigaoge550"
  * git config user.email "lizaigaoge550@gmail.com"
  * git commit -m 'initial commit'
  * git remote set-url origin https://github.com/lizaigaoge550/reduct_Dimension.git
  * git push -u origin master
 
