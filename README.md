# 档案管理系统

## 运行流程
```
1. yarn install
2. yarn run serve
```

## 登录说明

账户:admin 
密码: 123

## 项目介绍

`大学生档案系统` 是采用`Springboot` + `Vue2.0` + `ElementUI` 搭建的前后端分离项目。

项目分为个人信息、个人健康档案、健康建议、健康知识阅读、健康档案管理、角色管理、用户信息管理、权限管理等8个模块，可通过权限管理对不同角色授权达到不同角色登录系统时查看到
的模块信息不同，还可对不同的角色配置按钮级权限，让不同的角色再相同的页面有不同的操作权限。

用户注册时可选择普通用户或者医生角色进行注册。

> 普通用户

普通用户登录以后需要先完善自己的个人档案信息，也可以查看医生对自己的健康建议。还可阅读医生发布的健康知识文章，增加自己对健康这一块的意识。当完善个人健康档案以后
则需要等待对应科室医生对自己的档案相关检查信息进行完善。完善以后就可在个人信息那里查看到自己的健康分析图。

> 医生

医生可进行发布健康知识阅读相关的文章，也可在健康档案管理那里进行用户档案信息完善，再档案的尾部，医生可经过档案信息给出自己的合理意见。给出的意见会显示再健康建议模块那里
医生可查看自己的建议是否被用户查看等。

> 管理员

拥有全部权限，可进行角色授权，用户管理等全部的权限。


