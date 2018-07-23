# Ansible Google Next 2018 Demo!

The following content was adapted from [Compute Video Demo](https://github.com/GoogleCloudPlatform/compute-video-demo-ansible) - content prerequisites are listed there. Automation is now broken out into roles and makes use of role dynamic variable inclusion. Make chrome your default browser for a photo finish! 

Google Compute Variables
--------------
Relevant Google Compute variables are now limited to the scope of a role that requires them. Because the authentication variables need to be globally available across roles, it makes sense to have them in group_vars/all.
```
# Google Compute Engine required authentication global variables
project_id: <project_id>
service_account_email: demo-ansible@<project_id>.iam.gserviceaccount.com
credentials_file: '<path_to_credentials>'

# Variables to be set for dynamic hosts
ansible_ssh_user: <ansible_control_user>
ansible_ssh_private_key_file: ~/.ssh/google_compute_engine
```

Environment Variables
--------------
Previously the following environment variables needed to be exported:
```
export ANSIBLE_HOSTS=ansible_hosts
export ANSIBLE_HOST_KEY_CHECKING=False
```

These are now handled by setting their appropriate ansible.cfg equivalents:
```
[defaults]
inventory=hosts
host_key_checking=False
retry_files_enabled=False
```

Demo Time
--------------
The following playbook kicks off the demo:
```
ansible-playbook google-next-demo.yml
```

And this playbook cleans up all provisioned resources:
```
ansible-playbook cleanup.yml
```
