# Install CA Certs Role

This Ansible role installs CA certificates on Linux systems, specifically supporting Debian/Ubuntu and Red Hat-based distributions. It ensures that the necessary packages are installed and the trust directories are properly configured.

## Role Variables

- `ca_certificates`: A list of CA certificates to install. Each item can be a string path/URL or a dictionary with `src` and optional `dest_name`.

### Example

```yaml
ca_certificates:
  - src: "my-ca.crt"                    # local file from roles files folder (will be copied)
  - src: "/path/to/my-ca.crt"           # local file (will be copied)
  - src: "https://example.com/ca.pem"   # remote file (will be downloaded)
    dest_name: "example-ca.crt"         # stored as example-ca.crt on target
```

## Usage

Include the role in your playbook and define the `ca_certificates` variable as needed:

```yaml
- hosts: all
  roles:
    - role: joe-speedboat.install_ca_certs
      vars:
        ca_certificates:
          - "ca_demo.crt"
```

## Supported Platforms

- Debian/Ubuntu
- Red Hat Enterprise Linux (RHEL) 8, 9, 10
- AlmaLinux, Rocky Linux

## Handlers

- `Update CA certificates (Debian)`: Runs `update-ca-certificates` on Debian-based systems.
- `Update CA certificates (RedHat)`: Runs `update-ca-trust` on Red Hat-based systems.
