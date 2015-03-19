---
layout: post
title: "在MAC上搭建IONIC开发环境"
date: 2015-03-20
---
<html>
<body>
<p>前些日子按照IONIC官方文档指引，在MAC上搭建IONIC开发环境，但实际上出现了一些Tutorial没有出现的问题，有的问题甚至是因为搭建顺序不同引起的。不过总体来讲，MAC OSX上遇到的问题比Windows下问题少多了。以下是大致的流程<br/>
1.确认安装环境：我的是:<br/>
      Macbook OSX Yosemite:Version 10.10.1 <br/>
      64位机器<br/>
      PS：怎样知道MAC是64或32位？  在terminal 中打uname -m 如果显示的事x86_64 则是64位的<br/>
      <em>以下步骤中牵涉到软件版本时，要确认安装和自己机器位数相同的软件版本</em>
2. 卸载NODE（如果机器上没有安装NODEJS,则直接跳到第二步）: 打开terminal，运行以下脚本<br/>
	lsbom -f -l -s -pf /var/db/receipts/org.nodejs.pkg.bom | while read f; do  sudo rm /usr/local/${f}; done
	sudo rm -rf /usr/local/lib/node /usr/local/lib/node_modules /var/db/receipts/org.nodejs.*
	<br/>
3. 卸载NVM和NPM(若机器上未安装NVM，则直接跳到第三步)<br/>
   打开terminal，逐次运行以下命令（看个人配置，有可能需要加sudo前缀）<br/>
    	rm -rf ~/.nvm<br/>
    	rm -rf ~/.npm<br/>
    	rm -rf ~/.bower<br/>
    	rm -rf $NVM_DIR ~/.npm ~/.bower<br/>
4. Homebrew是一款广受好评的备软件管理神器，要紧跟世界潮流，我们也先安装Homebr/ew.<br/>
   打开terminal: 运行<em>ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebr/ew/install/master/install)"</em><br/>
5. 通过brew安装Nvm <br/>
   $ brew install nvm <br/>
   为了能使Terminal识别nvm，我们需要：<br/>
   $ echo "source $(brew --prefix nvm)/nvm.sh" >> ~/.zshrc <br/>
6. 通过NVM安装NPM <br/>
   先看下REMOTE上有哪些版本：$ nvm ls-remote <br/>
   选一个版本安装：$ nvm install -s v0.12.0 <br/>
   可以将nvm的缺省版本：$ nvm alias default 0.12.0
7. 安装Ionic, Cordova, Gulp等 <br/>
   npm install -g cordova, ionic, gulp  <br/>
8. 接下来就可以参考IONIC官网上的TUTORIAL来学习了。<br/>
   ionic start myapp blank<br/>
   cd myapp<br/>
   ionic platform add ios<br/>
   ionic build ios<br/>
   ionic emulate ios<br/>
9.步骤7、8过程中可能遇到的问题以及解决方案：<br/>
      9.1 Agreeing to the Xcode/iOS license requires admin privileges, please re-run as root via sudo.<br/> 
      解决：启动XCODE， AGREE <br/>
      9.2 Error: ios-sim was not found <br/>   
	 解决：sudo npm install ios-sim -g <br/>
      9.3 Local gulp not found in <br/>
	 解决： $ npm install --save-dev gulp    <br/>		   	 
	 参考：https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md  <br/>	
      9.4 如果遇到"Can't get Gulp to run: cannot find module 'gulp-util'" 
	 解决：则在工程文件夹下面执行:npm install <br/> 
         然后执行：gulp sass<br/>
         参考: http://stackoverflow.com/questions/21406738/cant-get-gulp-to-run-cannot-find-module-gulp-util <br/>
</p>
</body>
</html>
