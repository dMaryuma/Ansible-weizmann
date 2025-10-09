# Ansible-weizmann
Ansible playbooks to manage qtree/quota/ntfs permissions

## Requirements
* ansible [core 2.15.13+]
* python 3.9+
* python netapp-lib package from https://pypi.org/project/netapp-lib/
* netapp.ontap ansible module from: https://galaxy.ansible.com/ui/repo/published/netapp/ontap/ (v23.1.0+)

## Getting started
run every playbook with corresponding vars file, example:
```
ansible-playbook set_ntfs_permission.yaml -e@set_ntfs_permission_vars.yaml
ansible-playbook create_qtree.yaml -e @create_qtree_vars.yaml
```
### NetApp Custom Role
you can create custom role for that specific scenario
#### create role
```
cluster1::> security login role create -role ansible-role -cmddirname "volume qtree" -access all
cluster1::> security login role create -role ansible-role -cmddirname "volume quota" -access all
cluster1::> security login role create -role ansible-role -cmddirname "vserver security file-directory" -access all
cluster1::> security login role modify -role ansible-role -cmddirname DEFAULT -access readonly
```
#### create user with role
```
cluster1::> security login create -user-or-group-name ansible-user -application http -authentication-method password -role ansible-role
cluster1::> security login create -user-or-group-name ansible-user -application ontapi -authentication-method password -role ansible-role
```
