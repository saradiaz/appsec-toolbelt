#Dependency-check
This dependency checker from OWASP is widely used and actively developed. It is compatible with Java/.NET, and there is currently experimental support other languages including Python.

###Installation
There are a few ways to install dependency-check, but our best experience has been installing with Homebrew:

`$ brew update && brew install dependency-check`

You can also download the [dependency-check-cli](https://bintray.com/jeremy-long/owasp/dependency-check) zip file.

###Usage
Dependency-check requires two arguments:  

- `--scan` (path to project you would like to scan) 
- `--project` (choose the name you would like for your project)

Check out the `--advancedHelp` option for some very specific options that could be well-suited to your project.

With Python projects, it is advisable to use the `--enableExperimental` flag since the features that scan Python files are still considered experimental by the Dependency Check project (don't worry, we're pretty confident in it regardless).

By default, the HTML report will be saved to whatever directory you are in when you run the scan. This file will be overwritten if no `-o/--output` or `-f/--format` are specified. Keep this in mind if you integrate this into your pipeline (as we hope you do!).

###Documentation
The full documentation and the latest downloads can be found at: <https://jeremylong.github.io/DependencyCheck/index.html> 

###CI Integration
Some basic best practices/guidelines for adding OWASP Dependency Check to your CI pipeline can be found here:  
<https://github.com/cairnsc/security-playbook/blob/master/tooling/dependency-checker/owasp-dependency-check.md>