# Dependency Checkers

### bundler-audit
`gem install bundler-audit`  

##### Usage:  
`bundle-audit check` (check is optional if you are in the target repository)  
  
`bundle-audit check --verbose --update` will print out additional information about the identified vulnerability, as well as try to update to a secure version. (The `--update` option could be useful in a build pipeline.)

##### Best Practices:
Ideally, dependency checkers should be integrated into your build pipeline. Think of this as a test (a security test) that will run as your others do and fail if either:  

* You have vulnerable dependencies
* Updating your vulnerable dependencies causes another issue

This will, of course, depend on your configuration and what works best for your team.

##### Alternatively...
If your team uses a pre-commit script, you could run a bundler-audit check as part of that script.  

Keep in mind that, if you will be using the update option, it's probably a good idea to:  
1) run your tests  
2) run `bundle-audit --update`  
3) run your tests again so that you can difinitely tell if the update is what broke your tests. 