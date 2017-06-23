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
We see this more than you'd think. The dangers of checking secrets into your code are wide ranging and severe. It could lead to everything from an attacker compromising a user's session to full owning your application, and even the application server, gaining access to your database, and impersonating you to uncover more valuable data (and this is not an exhaustive list). 

I don't think you need to be scared into not checking secrets in -- you probably already understand that this is bad ([maybe][facepalm commit messages]).

[facepalm commit messages]: https://github.com/search?utf8=%E2%9C%93&q=add+secret+key&type=Commits

