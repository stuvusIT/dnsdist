# dnsdist

This role installs and configures PowerDNS dnsdist.
dnsdist is automatically restarted after configuration changes, unless the role variables say otherwise.

## Requirements

Debian 11 (Bullseye)

## Role Variables

| Name                   | Default/Required | Description                                                                           |
|------------------------|:----------------:|---------------------------------------------------------------------------------------|
| `dnsdist_repo_ver`     | `13`             | Version of the apt repository for dnsdist (Ubuntu only)                               |
| `dnsdist_config`       |                  | Configuration of dnsdist (will be put to the configuration file as-is)                |
| `dnsdist_restart`      | `true`           | Set this to false to prevent dnsdist from being restarted after configuration changes |
| `dnsdist_limit_nofile` | ` `              | Limit of file handles of dnsdist                                                      |

## Example Playbook

```yml
- hosts: dns
  roles:
  - dnsdist
     dnsdist_config: |
       setLocal('0.0.0.0:53', { toTCP=true, reusePort=true, })
       newServer({address="2001:4860:4860::8888", qps=1})
       setServerPolicy(firstAvailable)
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)
