# Security Baseline
Making a bullet-proof app is probably not feasible, and depending on what your app does, certain security measures might be even be overkill.

To make covering the basics easy, here's a set of guidelines that likely apply to your project:  

* No secrets in the code
* Use a dependency checker
* Validate user inputs
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

Are you using a tool that isn't in this repo? Are you developing with a language or framework not currently supported? Create an issue or submit a PR so we can get it added as quickly as possible. 

[owasp-a9]: https://www.owasp.org/index.php/Top_10_2013-A9-Using_Components_with_Known_Vulnerabilities

[Ruby]: https://github.com/saradiaz/appsec-toolbelt/blob/master/Ruby/dependency-checkers.md

[Java]: https://github.com/saradiaz/appsec-toolbelt/blob/master/Java/dependency-check.md

[JavaScript]: https://github.com/saradiaz/appsec-toolbelt/tree/master/JavaScript/dependency-checking

[Python]: https://github.com/saradiaz/appsec-toolbelt/blob/master/Python/dependency-check.md

## Validate User Inputs
If you have fields that accept user input in your application, making it a priority have some validations on this input is imperative to a basic level of security on your application. 

An [excellent blog][mfowler-webappsec-input] post by Cade Cairns and Daniel Somerfield outlines some of the dangers of accepting as-is user input, along with some mitigation strategies.

Here are some of the main takeaways:  

* Accepting unvalidated input can lead to an attacker taking control of the app itself.
* Setup alerts for potential attacks.
* Whitelist (positive validation) expected inputs **over** blacklisting a set of known unwanted inputs (negative validation). Make your whitelist strict.
* "Resist the temptation to filter out invalid input" aka "sanitization". **Reject invalid input altogether.** 

In a similar vein (and in the same blog post), take care to [encode HTML output][mfowler-webappsec-input] as well. 

[mfowler-webappsec-input]: https://martinfowler.com/articles/web-security-basics.html#RejectUnexpectedFormInput

[mfowler-webappsec-input]: https://martinfowler.com/articles/web-security-basics.html#EncodeHtmlOutput  

## No Production Data in Non-production Environments
Dev, QA, and staging environments (and their equivalents) often do not have the same care and security measures that are applied to a production environment. Additionally, this is where we do our testing -- where we break things and elicit unexpected behavior.

[Real Data in App Testing Poses Real Risks](http://www.darkreading.com/risk/real-data-in-app-testing-poses-real-risks/d/d-id/1129175?)  
[The Security Threat From Within](https://www.forbes.com/2009/12/14/virtualization-enterprise-software-technology-cio-network-security.html)

## Proper Access Controls
This one is tricky as it is very dependent on the context of your application. Here are some things to consider:  

* How do users authenticate? Are you using a [secure library][saml-vuln]?
* Should only privileged users have access to certain resources? Where are these roles stored? Could they be [manipulated by user input][mass-assignment]?
* What systems/services can access your database? 

This last point is absolutely critical. App context varies, but **an anonymous user/system/service should never be able to access your database**. Make sure there is a strong authentication model for your database.  

More Resources:  

* [OWASP Authentication Cheat Sheet](https://www.owasp.org/index.php/Authentication_Cheat_Sheet)
* [MongoDB](https://docs.mongodb.com/manual/security/)
* [AWS Elastic Search](https://aws.amazon.com/blogs/security/how-to-control-access-to-your-amazon-elasticsearch-service-domain/)
* [MySQL](https://dev.mysql.com/doc/refman/5.7/en/privilege-system.html)
* [PostgreSQL](https://www.postgresql.org/docs/9.4/static/auth-methods.html)
* [Microsoft SQL Server](https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/sql/authentication-in-sql-server)

[saml-vuln]: https://nvd.nist.gov/vuln/detail/CVE-2016-5697  
[mass-assignment]: https://www.owasp.org/index.php/Mass_Assignment_Cheat_Sheet  

## Enforce HTTPS Universally
You get this one! I know it. I *know* it. It's 2017, and we don't need convincing, right?

But did you know your application could *still* be [vulnerable to a MiTM attack][hsts-vid] if it isn't using [HSTS]?

[hsts-vid]: https://www.youtube.com/watch?v=zEV3HOuM_Vw
[HSTS]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security

## Enable Logging
Logs can help you detect and respond to potential malicious behavior in your application.  

[OWASP Logging Cheat Sheet](https://www.owasp.org/index.php/Logging_Cheat_Sheet#Purpose)  
[AWS CloudTrail](https://aws.amazon.com/blogs/aws/aws-cloudtrail-update-turn-on-in-all-regions-use-multiple-trails/)

