协同开发工具(版本控制器)
    目前使用最广泛的就是svn和git
    主要作用：管理项目的版本，多人协同开发
    svn和git帮我们管理项目
        svn：集中式
        git：分布式
    
SVN：
    1.打开服务器：注意事项：svn的服务器默认是80端口，所以和xampp的端口冲突
        推荐修改svn服务器端口：8989
        Configure logging -> network -> server port
    2.服务器端操作:(如果你安装失败了 ，就看看行了)
        1.创建仓库
        2.创建用户
        3.创建小组
    3.客户端操作
        1.远程无数据
            1.关联服务器：SVN检出
            2.提交到远程仓库：提交
            3.更新数据到本地：更新
        2.下载远程仓库数据：
            1.关联服务器：SVN检出
            2.提交到远程仓库：提交
            3.更新数据到本地：更新
        3.常见问题：版本冲突
            1.冲突产生的原因：服务器只能保存一个版本，不能同时保存多个版本
                index.js -> 版本1
                zhangsan -> 版本1 -> 版本2  --- 版本2
                lisi -> 版本1 -> 版本3
            2.手动解决冲突：
                对比文件，手动合并代码 -> 提交代码
            3.有效避免冲突
                与服务器保持版本一致：每次修改代码之前，先更新代码，然后在提交代码
                尽量不操作同一个文件：多人操作同一个文件导致的。如果是不同的文件，就不会有冲突的问题
        4.SVN图标问题
            1.图标不显示：https://jingyan.baidu.com/article/948f5924153366d80ff5f9fc.html
            2.图标的意义
Git:
    参考站点：https://www.liaoxuefeng.com/wiki/896043488029600/896067008724000
    git是目前世界上最先进的分布式版本控制系统
    集中式VS分布式
    Git应用：
        1.初始化git：
            git config --global user.name "Your Name"
            git config --global user.email "email@example.com"
        2.创建版本库：
            注意事项：如果你使用Windows系统，为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文。
            初始化版本库：git init
        3.版本库的管理：
            添加到缓存区：git add filename
            添加到版本库：git commit -m '注释'  注释必须写
        4.时光穿梭
            1.查看仓库状态：
                git status:查看看见是否被修改
                    modified(红色):未提交
                    modified(绿色):提交到了缓存区，但是没有添加到版本库
                git diff:查看具体修改的内容：
                    无论是add还是commit，都无法在查看数据的变化
            2.版本回退
                git log:查看历史提交版本
                git log --pretty=oneline:简化
                git reset --hard HEAD^：版本回退，^一个符号代表回退一个版本
                git reset --hard 版本号
            3.工作区和暂存区(缓存区)
                工作区：当前写的代码的目录
                缓存区：git add添加到缓存区
                版本库：git commit添加到版本库
                注意：多次add  一次性commit
            4.管理修改与撤销
                1.单纯修改了文件，没有添加也没有提交
                    git checkout -- filename:撤销刚刚的操作，撤销到提交的最后一个版本
                2.修改了文件，并且执行了git add，但是没有提交
                    撤回add的操作：git reset HEAD filename
                    撤回文件修改：git checkout -- filename
                3.修改了文件，执行了add和commit
                    此时只能执行版本回退了
                    git reset --hard HEAD^
            5.删除文件
                1.删除本地文件：rm filename
                2.删除仓库文件：
                    rm filename
                    git rm filename
                    git commit
                3.撤销删除
                    rm filename
                    git checkout -- filename
        5.分支管理：
            分支目前在使用过程中主要有两种方式：
                1.子分支作为每个人的开发分支，避免影响主分支及他人
                2.子分支也可以做i为一个标准的版本进行存储
                    例子：swiper：2.x  3.x  4.x都是子分支
            1.创建并切换到分支：git checkout -b name
                分支就是复制了一份主分支的内容，开辟了一个新的空间进行存储，此空间就是子分值
            2.切换到主分支：git  checkout master
            3.合并分支：git merge dev
            4.删除子分支：git branch -d name
            5.查看分支：git branch
            6.创建子分值：git branch name
        6.分支冲突解决：
            版本库只能存在一个版本
            版本冲突的实质就是同时操作一个文件
            手动解决冲突，合并两个人版本，然后删除不要部分，然后add commit
            为了避免冲突，大家还是要避免操作同一个文件