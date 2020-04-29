[![Build Status](https://travis-ci.org/open-io/ansible-role-openio-xcute.svg?branch=20.04)](https://travis-ci.org/open-io/ansible-role-openio-xcute)
# Ansible role `xcute`

An Ansible role for configure OpenIO xcute.

## Requirements

- Ansible 2.5+

## Role Variables


| Variable   | Default | Comments (type)  |
| :---       | :---    | :---             |
| `openio_xcute_beanstalkd_address` | `"beanstalk://{{ openio_xcute_bind_address }}:6014"` | URL of queue service |
| `openio_xcute_bind_address` | `openio_bind_address` | Address IP to use. |
| `openio_xcute_bind_interface` | `ansible_default_ipv4.alias` | Interface to use. |
| `openio_xcute_bind_port` | `6400` | Listening PORT |
| `openio_xcute_gridinit_dir` | `"/etc/gridinit.d/{{ openio_xcute_namespace }}"` | Path to copy the gridinit conf |
| `openio_xcute_gridinit_file_prefix` | `""` | Maybe set it to {{ openio_xcute_namespace }}- for old gridinit's style |
| `openio_xcute_log_level` | `INFO` | Log Verbosity. |
| `openio_xcute_namespace` | `OPENIO` | Namespace |
| `openio_xcute_orchestrator_enabled` | `true` | Enable xcute-orchestrator. |
| `openio_xcute_provision_only` | `false` | Provision only without restarting services. |
| `openio_xcute_redis_inventory_groupname` | `redis` | Groupname of redis in inventory. |
| `openio_xcute_redis_standalone` | `""` | Set a standalone redis instance like `127.0.0.1:6379` |
| `openio_xcute_sentinel_master_name` | `"{{ openio_xcute_namespace }}-master-1"` | Sentinel master name (not compatible with openio_xcute_redis_standalone) |
| `openio_xcute_sentinels_hosts` | `` | List of sentinels IP:PORT |
| `openio_xcute_server_enabled` | `true` | Enable xcute-server. |
| `openio_xcute_serviceid` | `"0"` | ID in gridinit. |
| `openio_xcute_workers` | `1` | Number of worker. |

## Dependencies

No dependencies.

## Example Playbook

```yaml
- hosts: all
  become: true

  roles:
    - role: users
    - role: repo
    - role: gridinit
    - role: redis
    - role: xcute
      openio_xcute_redis_standalone: "{{ ansible_default_ipv4.address }}:6011"
```


```ini
[all]
node1 ansible_host=192.168.1.173
```

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome.
The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork.
Github can then easily create a PR based on that branch.

## License

GNU AFFERO GENERAL PUBLIC LICENSE, Version 3

## Contributors

- [Cedric DELGEHIER](https://github.com/cdelgehier) (maintainer)
- [Romain ACCIARI](https://github.com/racciari) (maintainer)
- [Vincent LEGOLL](https://github.com/vincent-legoll) (maintainer)
