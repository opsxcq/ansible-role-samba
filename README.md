# Samba role for ansible

This playbook created a samba container.

# Variables

- `name` - The name of the current container.
- `volumes` - Volume mappings

# Env variables

The variable `env` will be applied as the environment variables of the
container. Bellow some variables that you can use to configure the samba
container with it.

- `USERS` - List of users for the container, comma separated.
- Passwords, set the value to the user key, it will be set as the password.
- `SHARES_CONF` - Aditional configuration of the shares in the samba server.


# Example playbook

```yaml
- hosts: all
  vars:
    name: samba-test
    env:
      USERS: "opsxcq"
      opsxcq: "admin"
      SHARES_CONF: |
        [Temp]
        path = "/share/"
        read only = no
        writable = yes
        valid users = opsxcq
        write list = opsxcq
        admin users = opsxcq
    volumes:
      - "/tmp:/share"
  roles:
    - ospxcq.samba
```
