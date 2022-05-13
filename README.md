# f5_test1

This is a repo that uses Gitlab/gitlab-runner to run Ansible in a Docker container. 
>See `.gitlab-ci.yml` to follow the flow or to run the playbooks.

# Basic flow
- runs the as3-dr.yml (Dry Run), this calls the base template which has conditionals that calls other tmplates for the app type. The playbook also generates the json config so that it can be inspected. Ansible then posts the json to the BIGIP rest api with the DR flag to test it works.
- runs the as3.yml, this calls the base template which has conditionals that calls other tmplates for the app type. The playbook also generates the json config so that it can be inspected. Ansible then posts the json to the BIGIP rest api.

It builds a AS3 decliaration file from Jinja templates from a a vars data-model.


## To Do

Work on the git merge from dev to master - process.

Add more of the var lookups into the templates.

## What if

What if I have a vip/pool etc already configured on the BIGIP can you change it via automation and if yes can you then revert it back?

What if I have a VIP called web-vip-01 with the IP 10.0.0.1/32 and the automation changes the ip address to 10.1.1.2/32, can it then be backed out and reverted too 10.1.1.1/32?
