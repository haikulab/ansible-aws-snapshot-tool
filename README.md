ansible-aws-snapshot-tool for Debian/Ubuntu
============

Ansible role for installing [aws-snapshot-tool](git@github.com:haikulab/aws-snapshot-tool.git) on the system.

## Overwrite Default Variables

The `vars/main.yml` file should contain your list of packages you want to install in order to override defaults found in `defaults/main.yml`.

## Setting up AWS access

### Create a policy

Create permissions policy to allow use to action backups. Use the `iam.policy.sample` to create the policy.

### Create a user for the policy

Create a user and assign to it the policy from previous step.
