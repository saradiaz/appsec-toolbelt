##Rubocop
Rubocop is source code analysis tool. It is not specifically meant for finding security bugs, but can be configured to be useful for this purpose.  

One benefit of Rubocop is that it can act as your linter as well as provide some light security analysis. If you are using a framework like Rails or Sinatra, Brakeman or Dawnscanner (respectively) are probably better bets for security-specific analysis. 

That being said, Rubocop is highly configurable, and has [extensive documentation](https://rubocop.readthedocs.io/en/latest/). You can pick and choose which rules (aka cops) to use, and you can even write your own. 

###Installation
`$ gem install rubocop` ([More Details](https://rubocop.readthedocs.io/en/latest/installation/))

###Usage
Analyzing your files with Rubocop is as simple as running  
`$ rubocop`  
while in your project directory. Of course, there are some fancier options as well. Some particularly interesting ones for security purposes are:  

`--except`  Allows you to exclude particular cops or departments (the general category that cops reside in, i.e. Department = Layout, cops = SpaceBeforeComma, TrailingWhitespace, etc.)

`--only`  The opposite of the except option

`-D/--display-cop-names`  This will include the cop names in the output so you can see which cops are particularly useful and/or noisy. This might help you figure out which to use with `--except` and `--only`. 

Of course, you can find all of the other available options in the usual ways.

###Configuration
You can customize the config file, and even specify mulitple config files at runtime.  

You can also specify `inherit_from` in your .rubocop.yml config file. You can inherit from other files in your project, as well as a remote URL. 

//TODO: provide recommended .rubocop.yml