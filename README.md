# Mistral demo Workflow with Ansible, running on StackStorm

Example of StackStorm & Mistral Workflow running 3 separate Ansible playbooks in parallel and posting results from each execution to Slack.

> There is some way to run tasks inside Ansible playbook in parallel via [async-poll](http://docs.ansible.com/ansible/playbooks_async.html),
 but it doesn't give such freedom and flexibility.
 
 So here (in best traditions of biologists :biohazard_sign: :) we crossed two different tools (Ansible & Mistral) and got new useful features. 


## Installation

Install StackStorm Ansible & Slack integration packs:
```sh
st2 run packs.install packs=ansible,slack
```

Install this pack with Demo Mistral workflow and Ansible playbooks in it:
```sh
st2 run packs.install packs=st2mistral-and-ansible repo_url=armab/st2mistral-and-ansible
```


## Configuration

1.) Adjust Ansible configuration for your remote machines:
* `/etc/ansible/ansible.cfg`
* `/etc/ansible/hosts`

2.) Add Slack credentials in `/opt/stackstorm/packs/slack/config.yml` section: `post_message_action`

## Example commands:
```sh
st2 run st2mistral-and-ansible.update_all package_managers=pip
st2 run st2mistral-and-ansible.update_all package_managers=gem,npm,pip
```


## Results
### Slack Messages
![Slack messages](http://i.imgur.com/ULywhvP.png)
