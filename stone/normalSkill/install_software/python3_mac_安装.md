#python3（mac）系统安装与环境配置

引子：现在用的mac电脑上系统自带的是2.7版本的python，想用python3.5，需要自行安装，电脑上可以同时有2.7和3.5的版本2个版本的兼容可以使用，虚拟环境的方式（virtualenv）【python三大神器virtualenv, fabric, pip】。

**目录：**
> [1、安装操作](#install)
>
> [2、使用虚拟开发环境，隔离2，3版本](#virtual)
>
> [3、虚拟开发环境使用](#virtual_use)
>

##<a name="install"></a>1、安装操作
###1-1、使用homebrew安装python ->brew install python3

遇到的问题：

1、

	【Error: The `brew link` step did not complete successfully
	The formula built, but is not symlinked into /usr/local
	Could not symlink .
	/usr/local/opt is not writable.
	You can try again using:【brew link gdbm】
  
  
 参考信息：
 
 	【Following Alex' answer I was able to resolve this issue; 
 	seems this to be an issue non specific to the packages being 
 	installed but of the permissions of homebrew folders.
	sudo chown -R `whoami`:admin /usr/local/bin】


FROM:

	http://stackoverflow.com/questions/26647412/homebrew-could-not-symlink-usr-local-bin-is-not-writable

我的尝试：

	sudo chown -R `whoami`:admin /usr/local/bin
	
	
2、

	【python3 You must `brew link pkg-config gdbm` before python3 can be installed】
	
参考信息：

	http://www.dongcoder.com/detail-293244.html
	
我的尝试：
输入：【brew link pkg-config gdbm】

出现：/usr/local/share/man/man3 is not writable.

输入：【sudo chown -R het /usr/local/share/man/man3/】

出现：/usr/local/opt is not writable.

输入：【sudo chown -R het /usr/local/opt/】

出现：Error: Could not symlink .

输入：brew link gdbm

出现：Linking /usr/local/Cellar/gdbm/1.12... 12 symlinks created

输入：brew install python3
等待安装。。。
心得：【查找Google，按照英文提示尝试】

3、

	【Error: Your Xcode (8.0) is outdated.Please update to Xcode 8.2 (or delete it).Xcode can be updated from the App Store.】
	
参考信息：

	【It was an overly strict move, and after some debate the decision has been vastly loosened in 12aad5c136. It will be made generally available with the 1.0.4 release, which will be cut fairly soon. For now there are at least three workarounds:
	Probably the easiest: set the TRAVIS environment variable:
	export TRAVIS=1
	Manually check out the master branch;
	Manually check out the 1.0.2 tag.
	Sorry for the inconvenience.】
	
我的尝试：
	
	export TRAVIS=1

结果：出现问题4

4、

	【Error: Permission denied - /usr/local/etc/openssl/misc/c_hash
 	Warning: Bottle installation failed: building from source.】
 	
 参考信息：
 
 	FROM:---http://www.jianshu.com/p/d96feb47b05b

 我的尝试：

	【chmod -R 755 /usr/local/etc/openssl/misc】

结果：
还是有蛮多问题的，但是基本都是按照提示来处理就好，大多出现权限不够等等，如果755还是不可以，可以尝试777安装homebrew和python3基本耗时2个钟头，安装记录都在这里了，这个习惯需要坚持，这个习惯很好@——@

##<a name="virtual"></a>2、虚拟开发环境，隔离版本
1.安装Virtualenv，pip3 install virtualenv

tip：在安装的时候，应该存在pip2和pip3，python2和python3，但是修改路径不是很好，所以我采用添加版本号的方式，不加的话，mac系统会逐层查找，所有会找到系统自带的python2

[参考信息](https://segmentfault.com/a/1190000006118856)

##<a name="virtual_use"></a>3、虚拟开发环境使用
创建虚拟环境：virtualenv caogao ##创建一个caogao的文件夹

也可以指定虚拟环境的版本 virtualenv caogao --python=python3.6

激活虚拟环境：source ./bin/activate

关闭虚拟环境：deactivate


