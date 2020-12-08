Stouts.postfix
==============

[![Build Status](http://img.shields.io/travis/Stouts/Stouts.postfix.svg?style=flat-square)](https://travis-ci.org/Stouts/Stouts.postfix)
[![Galaxy](http://img.shields.io/badge/galaxy-Stouts.postfix-blue.svg?style=flat-square)](https://galaxy.ansible.com/Stouts/postfix/)

Ansible role which manage postfix

#### Requirements

Only tested on ubuntu for now.

#### Variables

```yaml
postfix_enabled: true # The role is enabled

postfix_smtpd_use_tls: true
postfix_myhostname: "{{ inventory_hostname }}"
postfix_myorigin: $myhostname
postfix_smtp_sasl_auth_enable: true
postfix_smtp_tls_cafile: "/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
postfix_relayhost:
postfix_mynetworks: "127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128"
postfix_inet_interfaces: loopback-only
postfix_mydestination: $mydomain, $myhostname, localhost.$mydomain, localhost
postfix_local_recipient_map: ""
postfix_smtp_sasl_security_options: ""

postfix_generic_maps: ""

# Relay all mail going to local users (e.g. root or cron) to another mail address
postfix_local_user_relay_address: ""

# Useful if you use a SMTP server for relay that doesn't allow
# arbitrary sender addresses.
postfix_rewrite_sender_address: ""

# Send a test mail to this address when Postfix configuration changes
postfix_send_test_mail_to: ""

postfix_smtp_sasl_user: "{{ansible_ssh_user|default('root')}}"
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
    # Example configuration for gmail
    postfix_relayhost: "[smtp.gmail.com]:587"
    postfix_smtp_sasl_user: myemail@gmail.com
    postfix_smtp_sasl_password: mypassword

```

#### License

Licensed under the MIT License. See the LICENSE file for details.

#### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/Stouts/Stouts.postfix/issues)!
