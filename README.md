# ansible_apt_settings

Setup apt settings, services and timers.

## Supported operating systems

* Ubuntu 16.04
* Ubuntu 18.04
* Ubuntu 20.04
* Debian 9
* Debian 10

## System requirements

* Systemd

## Tasks

* Optional: Setup apt-autoremove service and timer

## Role parameters

| Variable      | Type | Mandatory? | Default | Description           |
|---------------|------|------------|---------|-----------------------|
| apt_settings_autoremove_enabled | boolean | no | false | If true setup the apt-autoremove service and timer |

## Example Playbook

### Add to `requirements.yml`:

```yaml
- name: setup-apt-settings
  src: https://github.com/borisskert/ansible_apt_settings.git
  scm: git
```

### Example `playbook.yml`:

```yaml
- hosts: servers
  roles:
  - role: setup-apt-settings
    apt_settings_autoremove_enabled: true
```

## Testing

Requirements:

* [Vagrant](https://www.vagrantup.com/)
* [Qemu](https://www.qemu.org/libvirt) and [libvirt](https://libvirt.org/)
* [Ansible](https://docs.ansible.com/)
* [Molecule](https://molecule.readthedocs.io/en/latest/index.html)
* [yamllint](https://yamllint.readthedocs.io/en/stable/#)
* [ansible-lint](https://docs.ansible.com/ansible-lint/)
* [Docker](https://docs.docker.com/)

### Run within docker

```shell script
molecule test --parallel && molecule test --scenario-name enable-autoremove --parallel
```

### Run within Vagrant

```shell script
molecule test --scenario-name vagrant-enable-autoremove --parallel
```

I recommend to use [pyenv](https://github.com/pyenv/pyenv) for local testing.
Within the Github Actions pipeline I use [my own molecule Docker image](https://github.com/borisskert/docker-molecule).

## License

MIT

## Author Information

* [borisskert](https://github.com/borisskert)
