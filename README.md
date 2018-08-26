# Ansible Role: Lynis

[![Build Status](https://img.shields.io/travis/infothrill/ansible-role-lynis/master.svg?label=travis_master)](https://travis-ci.org/infothrill/ansible-role-lynis)
[![Build Status](https://img.shields.io/travis/infothrill/ansible-role-lynis/develop.svg?label=travis_develop)](https://travis-ci.org/infothrill/ansible-role-lynis)
[![Updates](https://pyup.io/repos/github/infothrill/ansible-role-lynis/shield.svg)](https://pyup.io/repos/github/infothrill/ansible-role-lynis/)
[![Ansible Role](https://img.shields.io/ansible/role/25378.svg)](https://galaxy.ansible.com/infothrill/lynis/)


An [Ansible](http://www.ansible.com) role to install [Lynis](https://cisofy.com/lynis/),
an open source security auditing tool.

## Quick howto

requirements.yml:

    - src: infothrill.lynis
      version: v2.0.0

Install:

    ansible-galaxy install -r requirements.yml -p ./roles/

Playbook:

    - hosts: servers
        roles:
          - role: infothrill.lynis


## Role Variables

```yml
lynis_version: 2.6.8
lynis_version_sha256sum: 2e4c5157a4f2d9bb37d3f0f1f5bea03f92233a2a7d4df6eddf231a784087dfac
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
The directory for the Lynis logs. Used by the cron job. By default, Lynis will
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
lynis_cron_month: "*"
lynis_cron_day: "*"
lynis_cron_weekday: "*"
lynis_cron_hour: 3
lynis_cron_minute: 30
```
Lynis cron job configuration. The report, report log, and report data are
all written to the `lynis_log_directory`.

```yml
lynis_cron_rotate: 14
```
How many logs to keep in rotation (only meaningful when `lynis_cron` is true).

```yml
lynis_cron_initial_run: false
```
Set this to true to trigger an initial cron job run after initial
installation or version change of lynis.

## Dependencies

None.

## License

MIT

## Author Information

This role was forked from https://github.com/tommarshall/ansible-role-lynis
in 2018 by Paul Kremer.

## Changes

### v2.0.0

* added feature to run lynis on initial install or version change (`lynis_cron_initial_run`)
* renamed variable `lynis_rotate` to `lynis_cron_rotate`
* removed molecule playbooks that are just upstream copies

### v1.2.0

* expanded cron configuration options
* updated lynis default version to 2.6.8

### v1.1

* drop support for EOL ansible version 2.2 and 2.3
* upgrade molecule

### v1.0

* initial release
