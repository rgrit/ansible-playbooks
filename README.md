
---

# Infrastructure Automation Scripts

Welcome to the repository for automation scripts designed to streamline infrastructure management using Ansible and other tools. This repository contains scripts and configurations aimed at automating routine tasks across your infrastructure components, ensuring consistency and efficiency.

## Overview

Automation plays a crucial role in modern IT operations by reducing manual effort, minimizing errors, and enabling scalability. This repository houses Ansible playbooks and related configurations that automate tasks such as updates, configuration management, and more on your infrastructure.

## Contents

### `hosts.ini`

The `hosts.ini` file serves as the Ansible inventory, listing all managed hosts with their respective configurations.

Example content:

```ini
[all_hosts]
server1 ansible_host=192.168.1.101 ansible_user=admin ansible_port=22
server2 ansible_host=192.168.1.102 ansible_user=admin ansible_port=22
database ansible_host=192.168.1.103 ansible_user=dbadmin ansible_port=22
```

### `auto-update-playbook.yml`

This playbook automates the update process for all hosts listed in `hosts.ini`. It ensures that all systems are up-to-date with the latest patches and software versions.

Example playbook content:

```yaml
---
- name: Update all hosts
  hosts: all_hosts
  become: yes
  tasks:
    - name: Update apt repository cache
      apt:
        update_cache: yes
    
    - name: Upgrade all apt packages
      apt:
        upgrade: dist
```

## Getting Started

To use these automation scripts effectively, follow these steps:

1. **Clone the Repository:**

   ```sh
   git clone https://github.com/rgrit/ansible-playbooks.git
   cd ansible-playbooks/auto-update-playbook
   ```

2. **Edit `hosts.ini`:**

   Update the `hosts.ini` file with your actual host configurations, ensuring correct IP addresses, usernames, and SSH ports.

3. **Run Playbooks:**

   Execute the desired playbook using Ansible. For example, to run the `auto-update-playbook.yml`:

   ```sh
   ansible-playbook -i hosts.ini auto-update-playbook.yml
   ```

   Ensure you have SSH access and necessary permissions configured on all target hosts (`sudo` setup if applicable).

## Contributing

Contributions to improve and expand these automation scripts are welcome! If you have ideas for additional automation tasks or improvements, feel free to fork this repository, make your changes, and submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE). Feel free to use, modify, and distribute this code as per the terms.

## Acknowledgments

- Thanks to the Ansible community for providing powerful automation tools.
- Inspiration from the need to streamline and enhance infrastructure management processes.

---

Feel free to customize the content further based on your specific environment, tools, and processes. This README provides a clear introduction to your automation scripts, instructions for usage, and guidelines for contributions, making it easier for others (including your team members) to understand and utilize the scripts effectively.
