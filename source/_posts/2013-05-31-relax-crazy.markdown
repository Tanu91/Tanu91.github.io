---
layout: post
title: "Setting Up Octopress-BLOGGING fRAMEWORK"
date: 2013-05-31 14:50
comments: true
categories: 
---
{% img left http://cdn.tutsplus.com/webdesign.tutsplus.com/authors/ian-yates/octopress-header.png 150 250 %}


 You should be comfortable running shell commands and familiar with the basics of GIT.
GIT is a distributed Version Control System(VCS). This allows non-linear development of projects and can handle large amount of data effectively by storing it on Local Server.

Step 1: Install Git
	
	{% codeblock %}
	sudo apt-get insatll git
	{% endcodeblock %}
	
	  sudo-  for administrative previlages.
	apt-get - Package Installer, puts stuff from repositries and install them 
	
	Now it's time to configure your settings. To do this you need to open an app called Terminal.

	USERNAME
	    First you need to tell git your name, so that it can properly label the commits you make.
	
	{% codeblock %}
	git config --global user.name "Your Name Here"
	# Sets the default name for git to use when you commit
	{% endcodeblock %}
	
	E-Mail
	   Git saves your email address into the commits you make. We use the email address to associate your commits with your GitHub account.
	{% codeblock %}
	git config --global user.email "your_email@example.com"
	# Sets the default email for git to use when you commit
	{% endcodeblock %}

	To see all settings
	
	{% codeblock %}
	git config --list
	{% endcodeblock %}
	

