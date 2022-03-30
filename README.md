# Ansible Role for SSH

Deliberately simple Ansible role for managing _ssh_.

This is a _very_ rudimentary role with limited features.

This role simply manages the `sshd_config` file template using _lists_. The
content is free-form, as long as it validates.

Note: This only manages the config file and service. It does not manage the
package installation or the SSH _client_ configuration (currently).

## Installation

```yaml
roles:
  - src: https://github.com/joshbeard/ansible-role-ssh.git
    scm: git
    version: '0.1.0'
    name: jbeard.ssh
```

## Usage

### Variables

Refer to [`defaults/main.yml`](defaults/main.yml) for a listing and defaults of
variables used by this module. See [`vars/`](vars/) for OS-specific defaults.

The two primary variables used for `sshd` configuration are:

| Variable             | Description
| -------------------- | --------------------------------------------------------- |
| `sshd_config_common` | List of `sshd_config` options that are common across nodes.
| `sshd_config`        | List of extra `sshd_config` options to append to the common options.

Additionally, a `sshd_allow_groups` variable is available for setting the
`AllowGroups` config option, which can also be set with `sshd_config` or used
independently for greater flexibility.
