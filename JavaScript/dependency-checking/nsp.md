#NSP
Node Security Project (nsp) checks the dependencies in your project's package.json against libraries of known vulnerabilities. If your project uses vulnerable versions of a dependency, it will let you know and provide helpful details.

###Installation
`$ npm install --save-dev nsp`

###Usage
Running `$ nsp check` inside your project will generate a well formatted report in stdout

You can of course us the `-o/--output` option to write the results to a file. 

###CI Integration
Some basic best practices and guidelines for adding nsp to your CI pipeline can be found here:
<https://github.com/cairnsc/security-playbook/blob/master/tooling/dependency-checker/npm-dependency-checkers.md>