---
layout: post
title: "在MAC上搭建IONIC开发环境"
date: 2015-03-20
---
<html>
<body>
<p>前些日子按照IONIC官方文档指引，在MAC上搭建IONIC开发环境，但实际上出现了一些Tutorial没有出现的问题。以下是大致的流程<br/>
1. 卸载NODE（如果机器上没有安装NODEJS,则直接跳到第二步）: 打开terminal，运行以下脚本<br/>
	lsbom -f -l -s -pf /var/db/receipts/org.nodejs.pkg.bom | while read f; do  sudo rm /usr/local/${f}; done
	sudo rm -rf /usr/local/lib/node /usr/local/lib/node_modules /var/db/receipts/org.nodejs.*
	<br/>
2. 卸载NVM和NPM(若机器上未安装NVM，则直接跳到第三步)<br/>
   打开terminal，逐次运行以下命令（看个人配置，有可能需要加sudo前缀）<br/>
    	rm -rf ~/.nvm<br/>
    	rm -rf ~/.npm<br/>
    	rm -rf ~/.bower<br/>
    	rm -rf $NVM_DIR ~/.npm ~/.bower<br/>
 3. Homebr/ew是一款广受好评的备软件管理神器，要紧跟世界潮流，我们也先安装Homebr/ew.<br/>
   打开terminal: 运行<em>ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebr/ew/install/master/install)"</em><br/>
</p>
</body>
</html>
