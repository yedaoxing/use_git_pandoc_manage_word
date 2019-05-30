介绍一下背景：
	最近堂妹快毕业了，发给我的截图里面发现好多WORD文档啊，想起当年毕业的时候因为word格式和版本问题
	被骂的头破血流，头铁没破，但心真的在滴血，最近在用git管理代码，这是一个分布式版本控制系统，
	英文名是Version control system,缩写是VCS。如果你不理解这些话没关系，我接下来要做的是让你的
	word文档具有月光宝盒一样的穿梭能力，专业术语叫版本回退
上网查了一下找到两份参考资料：	
	http://blog.martinfenner.org/2014/08/25/using-microsoft-word-with-git/
	https://www.jianshu.com/p/fb72861ed7a5

开始环境配置：
	测试环境是windows10+git2.21.0+pandoc2.7.2
	谁来给台macos我测试一下，linux反正好友列表里没人玩不测试也罢，浪费时间
	
软件安装问题：
	git下载：
		https://git-scm.com/download/win
	pandoc下载：不好意思，我测试了一下，因为是国外的网站，偶尔会打不开，如果你那么不幸
	刚好登不上（原因就不说了，说了你也不懂），我准备了百度云你就当作是国内镜像吧，如果你知道
	国内其他镜像麻烦告知一下，这个网站我打好几次才打开
		https://pandoc.org/installing.html
		
环境配置问题
	git安装，一路确定就好
		检查git是否安装好
			打开命令行：super+r
				输入cmd。comand line的缩写是命令行的意思
					输入git，如果没出现找不到。。。命名，那就成了
					想装X一下？git --version
						就会显示你的git版本了
	pandoc安装，同样一路确定，这里记一下安装的路径，重点！！！要考！！！
		配置pandoc环境变量
			找到pandoc安装路径我的是：C:\Program Files\Pandoc
			super+E打开资源管理器，或者你直接点开也行
			鼠标右键我的电脑
				点击属性
					高级系统设置
						环境变量
							选path，path就是路径的意思
								编辑
									新建
										把前面要考的内容给我复制粘贴
											确定，环境变量配置成功			
			
在你的git仓库下面添加下面文件，一下内容来自：http://blog.martinfenner.org/2014/08/25/using-microsoft-word-with-git/
	# .gitattributes file in root folder of your git project
	*.docx diff=pandoc
	
	好啦我来解释一下上面的文字的意思
	#之后是注释，意思是说创建一个名字叫.gitattributes的文件内容为：
		*.docx diff=pandoc
	如果你知道*是通配符，说明计算机基础没白学，
	放在你的git仓库根目录下，不知道什么叫根目录，我录个视频给你看，不懂？
	那你准备一杯奶茶钱，我给你远程配置环境
	
	# .gitconfig file in your home folder
	[diff "pandoc"]
		textconv=pandoc --to=markdown
		prompt = false
	[alias]
		wdiff = diff --word-diff=color --unified=1
	我再来解释一下这个，算了不解释，我这个英语渣渣就不解释了，反正创建一个名字叫.gitconfig
	的文件放到你的家目录下，不知道什么叫家目录没关系，我待会录视频举个例子：
	名字叫Administrator的用户的家目录
		C:\Users\Administrator
	再来一个名字叫PETER的用户的家目录
		C:\Users\PETER
至此环境配置成功
好啦我的火气有点大，大半夜写这个东西我也是疯了，希望不要太迟，还能用一下。

接下来几个命令需要记一下：
git config --global user.name "你的名字，网名，郭靖黄蓉啥的都行，填在双引号内，哦！不能中文"
git config --global user.email "你的邮箱，随便填一个？如果你要使用github或者gitee就别乱填了，会无法推送的"
git init
	初始化仓库，初始化之后文件内的内容就可以开启月光宝盒功能了，init是initial的缩写？
	意思是初始化？反正我是这么记的
文件修改后需要两步创建穿梭点
git add 文件名
	我一般会偷懒git add .
		直接把当前目录全部内容添加，文件名可以打前几个字母然后用TAB键补全
git commit -am "写上你要写的话，作为你认识的标志"
	比如： git commit -am "这个就是最后版本了，打死也不改！算了算了，毕业重要"
		  git comit -am "终于毕业了，嗨森~"
			算了开个玩笑，不要用中文写标记了，会出现错误的，拼音Pinyin啥的就好
好啦，穿梭点设置好了，我们来查看一下穿梭点
git log 
	log 是日志的意思，就是使用git查看日志的意思？
	如果你没法推出查看日志，按下q键，quit推出的缩写
git reset --hard <commit version>
	不给自己加戏了，你们的压力很大的，我懂！
	回退到曾经提交过的版本
	比如我的
	git reset --hard 4c67f1a9aa
	git reset --hard aab730a23
	版本号是通过git log查到的，复制粘贴就行
git status
	查看当前到底干了什么东西
	
我只列我我觉得用的上的命令
git学习资料，就推荐progit看完第一章就够你用了，有中文版，不要方。
	https://git-scm.com/book/zh/v2
如果你觉得无聊可以看廖雪峰的git教程，这老哥比较皮：
	https://www.liaoxuefeng.com/wiki/896043488029600


