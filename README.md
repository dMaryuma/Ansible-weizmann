# Ansible-weizmann
Ansible playbooks to manage qtree/quota/ntfs permissions

## requirements
* ansible [core 2.15.13+]
* python 3.9+
* python netapp-lib package from https://pypi.org/project/netapp-lib/
* netapp.ontap ansible module from: https://galaxy.ansible.com/ui/repo/published/netapp/ontap/ (v23.1.0+)

## how to use?
run every playbook with corresponding vars file, example:
```
ansible-playbook set_ntfs_permission.yaml -e@set_ntfs_permission_vars.yaml
ansible-playbook create_qtree.yaml -e @create_qtree_vars.yaml
```
