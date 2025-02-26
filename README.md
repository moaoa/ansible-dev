# Ansible Server Setup

This Ansible playbook automates the installation of essential development tools on a server, including MySQL, PHP, Composer, Laravel, Node.js, Docker, Nginx, Neovim, Lazygit, and more.

## Prerequisites

- A Linux server (Ubuntu recommended)
- Ansible installed on your local machine
- SSH access to the server
- A user with `sudo` privileges

## Installation

### 1. Install Ansible (if not installed)

Run the following command on your local machine:

```bash
sudo apt update && sudo apt install -y ansible
```

Verify Ansible installation:

```bash
ansible --version
```

### 2. Clone or Copy the Repository

Copy the `install.yml` playbook file and the `hosts.ini` inventory file to your local machine.

### 3. Configure Inventory File

Create or edit the `hosts.ini` file to specify your server details:

```ini
[servers]
your_server_ip ansible_user=your_ssh_user
```

For local installation, use:

```ini
[servers]
localhost ansible_connection=local
```

### 4. Run the Playbook

To install the software on a remote server, run:

```bash
ansible-playbook -i hosts.ini install.yml
```

For local installation, run:

```bash
ansible-playbook -i localhost, --connection=local install.yml
```

### 5. Verify Installation

After running the playbook, verify the installation:

```bash
php -v
composer --version
node -v
docker --version
lazygit --version
```

### 6. Troubleshooting

- If Ansible fails due to SSH issues, ensure you can connect via SSH:

  ```bash
  ssh your_ssh_user@your_server_ip
  ```

- For debugging, add the `-vvv` flag to the playbook execution command:

  ```bash
  ansible-playbook -i hosts.ini install.yml -vvv
  ```

## Included Software

This playbook installs the following:

- **System Tools:** Git, Make, GCC, Unzip, Xclip
- **Database:** MySQL
- **Web Server:** Nginx
- **Programming Languages & Runtimes:** PHP, Node.js, npm
- **Development Tools:** Composer, Laravel, Neovim, Ripgrep, Lazygit
- **Containers:** Docker, Docker Compose

## Notes

- Ensure your firewall allows necessary ports (e.g., 80, 443 for Nginx, 3306 for MySQL).
- Some installations (e.g., Laravel) require `~/.composer/vendor/bin` to be added to the system PATH.

---

This script automates your development environment setup with Ansible. Feel free to modify it based on your requirements.

