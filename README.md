Stouts.postfix
==============

[![Build Status](https://travis-ci.org/Stouts/Stouts.postfix.png)](https://travis-ci.org/Stouts/Stouts.postfix)

Ansible role which manage postfix

#### Requirements

Only tested on ubuntu for now.

#### Variables

```yaml
postfix_enabled: yes # The role is enabled

postfix_smtpd_use_tls: yes
postfix_myhostname: "{{inventory_hostname}}"
postfix_smtp_sasl_auth_enable: yes
postfix_smtp_tls_cafile: "/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
postfix_relayhost: "[smtp.gmail.com]:587"
postfix_mynetworks: "127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128"
postfix_inet_interfaces: loopback-only

postfix_smtp_sasl_user: "{{ansible_ssh_user}}"
postfix_smtp_sasl_password: ""
```

#### Usage

Add `Stouts.postfix` to your roles and set vars in your playbook file.

Example:

```yaml

- hosts: all

  roles:
    - Stouts.postfix

  vars:
    postfix_smtp_sasl_user: myemail@gmail.com
    postfix_smtp_sasl_password: mypassword

```

#### License

Licensed under the MIT License. See the LICENSE file for details.

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Stouts/Stouts.postfix/issues)!
