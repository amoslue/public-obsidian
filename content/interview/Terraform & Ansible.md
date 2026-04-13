![[Pasted image 20260316141044.png]]


## Ansible
exmaple yaml: name + module + parameters

tasks:
```yaml
  - name: install nginx
    apt:
      name: nginx
```

Passing params:
```yaml
- name: install package
  apt:
    name: "{{ package_name }}"
    state: present
```

when using it, call the script with command: ansible-playbook playbook.yml -e "package_name=nginx" OR define under vars like
```yaml
- hosts: web
  become: yes

  vars:
    package_name: nginx

  tasks:
    - name: install package
      apt:
        name: "{{ package_name }}"
        state: present
```