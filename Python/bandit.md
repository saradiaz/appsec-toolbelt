# Bandit
Bandit is a static security analysis tool for Python. Bandit is meant to find the common issues, so please don't take a passing scan to mean bullet-proof code. You may want to use Bandit in conjunction with a language-agnositc analysis tool like Grepbugs.

Its [README.rst](https://github.com/openstack/bandit/blob/master/README.rst) is pretty great (somehow both extensive and succinct), so I won't say too much here. 

### Some Notes:  

**1)** When you have run a scan with bandit, be sure to pay special attention to the following lines in the output:

	Code scanned:  
		Total lines of code: 645  
		Total lines skipped (#nosec): 0  

Make sure those numbers make sense -- if you forget to set the -r option, bandit will not scan your project directories recursively. 

**2)** Similarly, try running bandit with the `--verbose` option the first time you run it (or whenever you are trying to debug). It lists files included in and excluded from the scan.