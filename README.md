# Ansible Role: Lynis

An [Ansible](http://www.ansible.com) role to install [Lynis](https://cisofy.com/lynis/),
an open source security auditing tool.

## Quick howto

requirements.yml:

	- src: infothrill.lynis
	  version: v1.0

Install:

	ansible-galaxy install -r requirements.yml -p ./roles/

Playbook:

    - hosts: servers
        roles:
		    - role: infothrill.lynis


## Role Variables

```yml
lynis_version: 2.6.3
lynis_version_sha256sum: df75f39abdbcf921d949dc9b8b1348fefb2ccca27bda9089a702312b0a7c3f31
```
The version and corresponding `sha256sum` of Lynis to install. Latest version
and hash can be found on the [Lynis download page](https://cisofy.com/download/lynis/).

```yml
lynis_directory: /opt/lynis
```
The directory to hold the Lynis installation.

```yml
lynis_log_directory: /var/log/lynis
```
The directory for the Lynis logs. Used by the cron job. By default Lynis will
output the report to `stdout` and log to `/var/log/lynis.log` and
`/var/log/lynis-report.dat`.

```yml
lynis_log_group: adm
```
The unix group that should own the generated logs.

```yml
lynis_config_directory: /etc/lynis
```
The directory to store cron related scripts and configuration.

```yml
lynis_cron: yes
lynis_cron_hour: 3
lynis_cron_weekday: "*"
lynis_cron_minute: 30
```
Lynis cron job configuration. The report, report log, and report data are all written to the `lynis_log_directory`.


## Dependencies

None.

## License

MIT

## Author Information

This role was forked from https://github.com/tommarshall/ansible-role-lynis
in 2018 by Paul Kremer.

## Changes

### v1.0

* initial release
