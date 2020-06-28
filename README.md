# aviSaml

## Goals
Ansible Playbook to configure Avi with SAML for enabling authentication/sso

## Prerequisites:
1. Make sure the controller is available at the IP defined in vars/creds.json
2. Make sure avisdk is installed:
```
pip install avisdk
ansible-galaxy install -f avinetworks.avisdk
```

## Environment:
Playbook(s) has/have been tested against:

### Ansible

```
avi@ansible:~/ansible/aviSlackAlerts$ ansible --version
ansible 2.9.5
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/home/avi/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /home/avi/.local/lib/python2.7/site-packages/ansible
  executable location = /home/avi/.local/bin/ansible
  python version = 2.7.12 (default, Oct  8 2019, 14:14:10) [GCC 5.4.0 20160609]
avi@ansible:~/ansible/aviSlackAlerts$
```

### Avi version

```
Avi 18.2.9
```

## Input/Parameters:

- All the paramaters/variables are stored in var/params.yml.
```
authProfile:
  - name: authProfile1
    type: AUTH_PROFILE_SAML
    saml:
      sp:
        saml_entity_type: AUTH_SAML_APP_VS

ssoPolicy:
  - name: ssoPolicy1
    type: SSO_TYPE_SAML
```

- The metadata file needs to be copied in the vars directory with the name "metadata"

## Use the ansible playbook to:
1. Create a new Auth Profile (SAML based)
2. Create a new SSO policy based on the auth profile

## Run the playbook:
ansible-playbook configureAlerts.yml

## Improvement:
Enable this for a list of vs or for all the vs already configured (default mode)
