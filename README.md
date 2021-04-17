# env_ansible
Ansible development/deployment environment in Remote Container

## Features

- Remote Containers environment for Visual Studio Code
- Development and deployment environment for Ansible and Jinja2
- Playbooks can be played under proxy environment with your ~/.ssh/ files
- VSCode extensions for Git (Graph / History / Lens) are ready

## Getting Started

### Prerequisites

- Host OS: Docker Compose and Visual Studio Code should be installed.
  - The followings were tested.
    - Ubuntu 20.04
    - Windows 10
- Docker Compose 1.25.5 or later
- Visual Studio Code 1.45 or later
- Internet connection
  - If under proxy, the following environment variables should be set and exported.
    - `http_proxy` and `https_proxy`
    - Each value shoud start with `http://` or `https://`
  - SSH connections shoud be reached to your target hosts.
    - The following SSH setting is a sample in `~/.ssh/config` under proxy environment.

```Shell:~/.ssh/config
Host *.my.domain
    ProxyCommand /usr/bin/nc -X connect -x 192.168.0.254:8080 %h %p
```

### Installing

1. Ensure "Remote Containers" extension is added in your Visual Studio Code.
2. Copy the file `.devcontainer/consts.env.sample` to `.devcontainer/consts.env` (ignored by git), and edit your own environments.
3. To use Ansible Vault, set your password to encrypt/decrypt to `ANSIBLE_VAULT_PASSWORD` in `.devcontainer/consts.env`.
4. If your UID  is not `1000`, set and export your UID value to environment variable `VSCODE_USER_ID`.

## Usage

- Open the top directory cloned with Visual Studio Code.
  - Use the menu "Remote-Containers: Open Folder in Container...".

## Note

1. your `~/.ssh/` directory is linked to `~vscode/.ssh/` in the container.
2. Ansible outputs logs to `.devcontainer/ansible/log/` in the host OS (ignored by git).

## Author

i3244

## License

MIT License
