# Unison
Unison synchronize.

## Requirements
No additional requirements.

## Role Variables
Settings have been throughly documented for usage.

[defaults/main.yml](https://github.com/r-pufky/ansible_unison/blob/main/defaults/main.yml).

## Dependencies
N/A

## Example Playbook
host_vars/client.example.com/vars/unison.yml
``` yaml
unison_config:
  username:
    home: '/etc/ca'
    targets: ['/srv/ca']
    sync: true
    config:
      ca_sync:
        root:
          - 'ssh://server.example.com//d/srv/ca'
          - '/srv/ca'
        auto:           true
        batch:          true
        fat:            true
        group:          true
        owner:          true
        silent:         true
        terse:          true
        times:          true
        confirmbigdel:  true
        contactquietly: true
        copymax:        1
        fastcheck:      true
        ignorearchives: true
        prefer:         'newer'
    cron:
      ca_sync:
        special_time: 'daily'
```

site.yml
``` yaml
- name:   'sync destination'
  hosts:  'server.example.com'
  become: true
  roles:
     - 'r_pufky.unison'

- name:   'sync source'
  hosts:  'client.example.com'
  become: true
  roles:
     - 'r_pufky.unison'
```

## Issues
Create a bug and provide as much information as possible.

Associate pull requests with a submitted bug.

## License
[AGPL-3.0 License](https://github.com/r-pufky/ansible_unison/blob/main/LICENSE)

## Author Information
https://keybase.io/rpufky
