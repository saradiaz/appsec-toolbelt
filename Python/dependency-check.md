# Dependency Checkers

## Safety
Safety a very strong choice for your Python project. It's easy to install, easy to use, and accumulates information from several sources to give you as much, or as little information as you need. Not to mention the README comes with a set of instructions for CI Pipeline integration :)

### Installation  
Classic.  
`$ pip install safety`  

### Usage
I find I get the best results when I explicitly tell Safety to look at my requirements file.  
`safety check -r requirements.txt`  
This will output the name, installed version, and affected version of the vulnerable dependency.  

If you're looking for more information, you can run a full report.  
`$ safety check -r requirements.txt --full-report`
This outputs the corresponding CVE, descriptions of the issue as collected from multiple sources, and even relevant links to follow for more details.  

If you are combining Safety with other vulnerability scanning tools, or if you are using it in your CI pipeline, it might make the most sense to output only the names of the vulnerable packages.  
`$ safety check -r requirements --bare` 

### Documentation
Check out the GitHub project: <https://github.com/pyupio/safety>

## OWASP Dependency Check
This dependency checker from OWASP is widely used and actively developed. It is compatible with Java/.NET, and there is currently experimental support other languages including Python. Given the experimental nature of the project at this time (July 21, 2017), Safety is likely a better option for your Python project.

### Installation
There are a few ways to install dependency-check, but our best experience has been installing with Homebrew:

`$ brew update && brew install dependency-check`

You can also download the [dependency-check-cli](https://bintray.com/jeremy-long/owasp/dependency-check) zip file.

### Usage
Dependency-check requires two arguments:  

- `--scan` (path to project you would like to scan) 
- `--project` (choose the name you would like for your project)

Check out the `--advancedHelp` option for some very specific options that could be well-suited to your project.

With Python projects, it is advisable to use the `--enableExperimental` flag since the features that scan Python files are still considered experimental by the Dependency Check project (don't worry, we're pretty confident in it regardless).

By default, the HTML report will be saved to whatever directory you are in when you run the scan. This file will be overwritten if no `-o/--output` or `-f/--format` are specified. Keep this in mind if you integrate this into your pipeline (as we hope you do!).

### Documentation
The full documentation and the latest downloads can be found at: <https://jeremylong.github.io/DependencyCheck/index.html> 