#GrepBugs
GrepBugs is a regex-based static analysis tool that looks for potentially dangerous methods and patterns in your code. Given that this is regex, it can be noisy, but the reports provide enough context to quickly weed out false positives. 

Another helpufl aspect of GrepBugs is that it gives you quick feedback about the numbers of file types, and even lines of code present.

###Installation & Usage
To install GrepBugs, you simply clone the GitHub repository:

`$ git clone https://github.com/foospidy/GrepBugs.git`

I'd recommend either:

* cloning it into your project folder
* placing it in your home directory and adding the following line to your .bash_profile:

`alias grepbugs ='python2 ~/Grepbugs/grepbugs.py'`

This will allow you to run a scan anywhere, all you have to do is set the target path:  
`$ grepbugs -d my/project`

###Other Notes
When you run a scan, the output will be created in the 'out/' folder. By default, two files will be created for every scan: .html and .txt

The default name for the scan will be the path you provided. 