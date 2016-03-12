# Ansible Gitlab CI Multi Runner

An Ansible provisioner I quickly hacked together to create new GitLab CI build servers for docker based workflows.

## Usage

To run with Vagrant you will first need a Gitlab.com CI token. Gitlab.com is the only supported host for Vagrant by
default, but you can override this by setting `ci_server` in the `ansible.extra_vars` object in the Vagrantfile. To run
with Vagrant you must specify your token as a environmental variable. This is because Vagrant will not run Ansible in
interactive mode, so the prompts will not work.

```
ANSIBLE_GITLAB_CI_RUNNER={{ YOUR_TOKEN }} vagrant provision
```

To run against a production server create a `hosts` file at the root of the project and add your servers in the
following format:

```
[build]
95.85.41.241 ansible_connection=ssh  ansible_ssh_user=root
```

Now run with `ansible-playbook -i hosts gitlab-runner.yml`
