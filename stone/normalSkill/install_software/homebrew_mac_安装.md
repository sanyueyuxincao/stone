#mac安装homebrew

遇到的问题1、

	 【HEAD is now at f7bccee Merge pull request #1801 from woodruffw/check-temp-correctly Error: 
	 /usr/local/Cellar is not writable. You should change the
	ownership and permissions of /usr/local/Cellar back to your
	user account: sudo chown -R $(whoami) /usr/local/Cellar 
	Failed during: /usr/local/bin/brew update --force】
	
处理方式：

sudo chown -R het /usr/local/Cellar

最终结果：

引出问题2


问题2、

	【Error: Could not link:
	/usr/local/share/doc/homebrew
	Please delete these paths and run `brew update`.
	Error: Failed to link all completions, docs and manpages:
	Permission denied - (../../../Homebrew/completions/zsh/_brew, /usr/local/
	share/zsh/site-functions/_brew)
	Failed during: /usr/local/bin/brew update --force】
	
处理方式：

rm -rf /usr/local/share/doc/homebrew


tips

1.安装方法->[homebrew官网安装](http://brew.sh/index_zh-cn.html)

2.查看安装版本->brew -v