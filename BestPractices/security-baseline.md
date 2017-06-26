# Security Baseline
Making a bullet-proof app is probably not feasible, and depending on what your app does, certain security measures might be even be overkill.

To make covering the basics easy, here's a set of guidelines that likely apply to your project:  

* No secrets in the code
* Use a dependency checker
* Encode/Sanitize your inputs
* No production data in non-prod environments
* Proper access controls
* Enforce HTTPS universally
* Enable logging


## No Secrets in the Code
We see this more than you'd think. The dangers of leaving secrets into your code are wide ranging and severe. It could lead to everything from an attacker compromising a user's session to full owning your application, and even the application server, gaining access to your database, and impersonating you to uncover more valuable data (and this is not an exhaustive list). 

I don't think you need to be scared into not checking secrets in -- you probably already understand that this is bad ([maybe][facepalm commit messages]), but here are your alternatives:

* Use environment variables ([some background][12-factor-app]; [in heroku][heroku-config-vars]; [in-gocd][go-envs])
* [credstash][credstash-details]
* [AWS Parameter Store][param-store]
* If you need to keep the secrets in your code, you can use [gitcrypt][gitcrypt-repo] to encrypt sensitive files on commit. 


[facepalm commit messages]: https://github.com/search?utf8=%E2%9C%93&q=add+secret+key&type=Commits

[credstash-details]: https://github.com/fugue/credstash#how-does-it-work

[gitcrypt-repo]: https://github.com/AGWA/git-crypt

[12-factor-app]: https://12factor.net/config

[param-store]: https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-paramstore.html

[heroku-config-vars]: https://devcenter.heroku.com/articles/config-vars

[go-envs]: https://docs.gocd.org/15.3.0/faq/dev_use_current_revision_in_build.html

## Use a Dependency Checker
Using components with known vulnerabilities is a [widespread and serious problem][owasp-a9] in application development. It can lead to easy, scannable vulnerabilities in your app. Recommended tools for a variety of languages are provided elsewhere in this project:  

* [Ruby]
* [Java]
* [JavaScript]
* [Python]

[owasp-a9]: https://www.owasp.org/index.php/Top_10_2013-A9-Using_Components_with_Known_Vulnerabilities

[Ruby]: https://github.com/saradiaz/appsec-toolbelt/blob/master/Ruby/dependency-checkers.md

[Java]: https://github.com/saradiaz/appsec-toolbelt/blob/master/Java/dependency-check.md

[JavaScript]: https://github.com/saradiaz/appsec-toolbelt/tree/master/JavaScript/dependency-checking

[Python]: https://github.com/saradiaz/appsec-toolbelt/blob/master/Python/dependency-check.md
