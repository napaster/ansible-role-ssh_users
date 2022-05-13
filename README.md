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

## Notice

Only one group deployed on one play. Use script to avoid this or sumbit PR.
