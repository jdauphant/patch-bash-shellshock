patch-bash-CVE-2014-7169
===========================

Patch bash with ansible 


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

# Test if you need to patch
```
% env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
vulnerable
this is a test
-> Your bash is vulnerable
% env x='() { :;}; echo vulnerable' bash -c "echo this is a test"                                                   ~/flaminem/project/ansible-playbooks julien@jd-pt
bash: warning: x: ignoring function definition attempt
bash: error importing function definition for `x'
this is a test
-> Your bash is not vulnerable
```

# More information
- CVE-2014-7169
- https://securityblog.redhat.com/2014/09/24/bash-specially-crafted-environment-variables-code-injection-attack/

# Author
Julien DAUPHANT
