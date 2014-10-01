patch-bash-shellshock
===========================

Patch bash #shellshock with ansible 


# Supported distributions
- Debian
- Ubuntu

# Usage :
    pip install ansible
    ansible-playbook -i your_inventory_file patch-bash-CVE-2014-7169.yml
    # or
    ansible-playbook -i "192.168.0.10," patch-bash-CVE-2014-7169.yml

your_inventory_file just need to contain your server list :
```
192.168.0.10
webserver1.example.com
webserver2.example.com
db1.example.com
```

# Test if you need to patch (tests are included in the playbook)
```
% wget https://raw.githubusercontent.com/hannob/bashcheck/master/bashcheck
% bash bashcheck
Vulnerable to CVE-2014-6271 (original shellshock)
Vulnerable to CVE-2014-7169 (taviso bug)
bashcheck: line 18:   664 Segmentation fault      (core dumped) bash -c "true $(printf '<<EOF %.0s' {1..79})" 2> /dev/null
Vulnerable to CVE-2014-7186 (redir_stack bug)
Test for CVE-2014-7187 not reliable without address sanitizer
Variable function parser still active, likely vulnerable to yet unknown parser bugs like CVE-2014-6277 (lcamtuf bug)
-> Your bash is vulnerable
% bash bashcheck                                              
Not vulnerable to CVE-2014-6271 (original shellshock)
Not vulnerable to CVE-2014-7169 (taviso bug)
Not vulnerable to CVE-2014-7186 (redir_stack bug)
Test for CVE-2014-7187 not reliable without address sanitizer
Variable function parser inactive, likely safe from unknown parser bugs
-> Your bash is not vulnerable
```

# More information
- CVE-2014-6271
- CVE-2014-7169
- CVE-2014-7186
- CVE-2014-7187
- https://securityblog.redhat.com/2014/09/24/bash-specially-crafted-environment-variables-code-injection-attack/
- https://github.com/hannob/bashcheck

# Author
Julien DAUPHANT
