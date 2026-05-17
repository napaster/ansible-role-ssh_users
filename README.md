# ansible-ssh_users

Role for manage users and her ssh keys. Support creation and deletions of users.
After deploy via ssh user can access only via ssh key. Root access or password
access will be disabled.

## Requirements

* Ansible 2.8+;

## How to work

Create dict, like this:

```yaml
users:
  user1:
    uid: '1000'
    rsa: 'ssh-rsa paste here'
    state: 'present'
  user2:
    uid: '1999'
    rsa: 'ssh-rsa paste here'
    state: 'absent'
robots:
  bot:
    uid: '1050'
    rsa: 'ssh-rsa paste here'
    state: 'present'
```

Run playbook:

```shell
ansible-playbook deploy_ssh_users.yml -e target_group=users
```

If `target_group` is not defined, role uses `admin` and deploys only
`napaster` by default:

```yaml
ssh_users_default_target_group: 'admin'
ssh_users_default_users:
  - 'napaster'
```

To deploy the full group, pass `target_group` explicitly. To deploy only
selected users from the target group, pass `target_users` or override
`ssh_users_default_users`.

## Notice

Only one group deployed on one play. Use script to avoid this or sumbit PR.
