# Генерация Ansible playbook (homework.yaml), inventory файла и test.txt

from pathlib import Path

# Содержимое inventory
inventory_content = ```
[netology-ml]
host1 ansible_host=192.168.1.101 ansible_user=ansible
host2 ansible_host=192.168.1.102 ansible_user=ansible```


# Содержимое playbook
playbook_content = ```\
---
- name: homework.yaml - Netology ML Deployment
  hosts: netology-ml
  become: true
  vars:
    packages:
      - net-tools
      - git
      - tree
      - htop
      - mc
      - vim
    users:
      - devops_1
      - test_1

  tasks:

    - name: Check connectivity
      ansible.builtin.ping:

    - name: Update package manager (apt)
      ansible.builtin.apt:
        update_cache: yes

    - name: Install required packages
      ansible.builtin.apt:
        name: "{{ packages }}"
        state: present

    - name: Copy test.txt to remote host
      ansible.builtin.copy:
        src: test.txt
        dest: /tmp/test.txt

    - name: Create user groups and users with home directories
      ansible.builtin.user:
        name: "{{ item }}"
        state: present
        create_home: yes
      loop: "{{ users }}"
```

# Пример содержимого test.txt
test_txt_content = "Привет из Ansible! Это файл test.txt\n"

# Сохраняем все файлы
Path("/mnt/data/inventory").write_text(inventory_content)

Path("/mnt/data/homework.yaml").write_text(playbook_content)

Path("/mnt/data/test.txt").write_text(test_txt_content)

"/mnt/data/"
