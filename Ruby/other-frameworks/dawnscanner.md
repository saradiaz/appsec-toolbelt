# Ruby Static Analysis Tools

## Dawnscanner
Dawnscanner is a source code security analysis tool that is compatible with __Rails, Sinatra, and Padrino__.

### Installation

#### Secure Download
The Dawnscanner rubygem is cryptographically signed. To be sure the gem you install hasn’t been tampered with, first add paolo@dawnscanner.org public signing certificate as trusted to your gem specific keyring. 

`$ gem cert --add <(curl -Ls https://raw.githubusercontent.com/thesp0nge/dawnscanner/master/certs/paolo_at_dawnscanner_dot_org.pem)`

`$ gem install dawnscanner -P MediumSecurity`

#### Else...
`$ gem install dawnscanner`  

//TODO: provide recommendations for usage and CI integration



