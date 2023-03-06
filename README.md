# Ansible Role: install_ca_certs
I found this role on ansible galaxy, but it had waiting pull requests and did not seem to get needed maintentance, so I took over.

## Description

Ansible role to manage CA certificates in the Linux and Windows system trust store. It's possible to add PEM formatted certificates from the local file system, a already trusted HTTP(s) URL, from raw content.


## Installation

```bash
ansible-galaxy install joe-speedboat.install_ca_certs
```

## Requirements

none

## Role Variables

### ca_certificates_root_directory

Location where the certificates are stored under windows before
they are imported into the certificate store of Windows.

```yml
ca_certificates_root_directory: '{{ ansible_env.TMP }}'
```

### ca_certificates_packages

Packages to be installed.

```yml
ca_certificates_packages:
  - ca-certificates
```

### ca_certificates_files

```yml
ca_certificates_files: []
```

## Dependencies

None

## Example Playbook
Look into test directory for an example:
```
ansible-playbook test.yml
```


# License

https://opensource.org/licenses/GPL-3.0
Copyright (c) Chris Ruettimann <chris@bitbull.ch>

