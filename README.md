# Binbash - Ansible Role: Jenkins Role-based Strategy

Ansible role for enabling and configuring Jenkins Role-based Strategy.

## Requirements
* Jenkins with Role-based Strategy plugin installed

## Examples
The following example defines a couple of users and assigns the built-in roles to each of them:
```
  - role: binbash_inc.ansible_role_jenkins_role_based_strategy
    jenkins_rbs_users:
    - name: user1
      roles:
      - admin
    - name: user2
      roles:
      - authenticated
```

The example below defines a custom roles and assigns it to a custom user:
```
  - role: binbash_inc.ansible_role_jenkins_role_based_strategy
    jenkins_rbs_roles:
    - name: app1-deployer
      type: RoleBasedAuthorizationStrategy.GLOBAL
      overwrite: "true"
      pattern: "app1-.*"
      permissions:
      - hudson.model.Hudson.Read
      - hudson.model.Item.Build
      - hudson.model.Item.Discover
      - hudson.model.Item.Read
    jenkins_rbs_users:
    - name: user1
      roles:
      - app1-deployer
```
