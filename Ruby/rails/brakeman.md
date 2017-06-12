# Brakeman 
Brakeman is a source code security analysis tool **for Rails projects**. 

One great aspect of brakeman is that, not only does it scan your code and alert you to potential security bugs, but it also provides extensive documentation to help you understand the dangers of each vulnerability. 

### Installation
`$ gem install brakeman`

### Usage
`$ brakeman my-project/`  
##### Useful Options
-A, --run-all-checks (Run all default and optional checks)  

-q, --quiet (Suppresses informational output)

--skip-files

-d, --debug

-k, --checks (List all available vulnerability checks)

-f, --format 

-o, --output 

--confidence-level (Set minimal confidence level to be reported (1 - 3). This option can be used to reduce noise and/or potential false positives.)

You can specify the Rails version with -4,5 etc (though please make sure your version of Rails is secure. You can check known vulnerabilities [here][rails_cve].)  

[rails_cve]:https://www.cvedetails.com/vulnerability-list/vendor_id-12043/product_id-22568/Rubyonrails-Ruby-On-Rails.html

##### My personal favorite way to run Brakeman if I've got time:
`$ brakeman my-project/ -A -f html -o brakeman-report-DATE.html`

##### My personal favorite way to run Brakeman if I've already run a few scans:
`$ brakeman my-project/ --faster -confidence-level 2 -f html -o brakeman-report-DATE.html`

Checkout further documentation on Brakeman options [here][brakeman_link].

[brakeman_link]:http://brakemanscanner.org/docs/options/


