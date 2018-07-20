# Google Next Demo

The following content was adapted from [Compute Video Demo](https://github.com/GoogleCloudPlatform/compute-video-demo-ansible) - content prerequisites are listed there. Content is broken out in roles and makes use dynamic variable inclusion. Make chrome your default browser for a photo finish! 

Google Compute Variables
--------------
Relevant Google Compute variables are now limited the scope of a role that requires them. Because the authentication variables need to be globally available across roles, it makes sense to have them there.
```
# Google Compute Engine required authentication global variables
project_id: <project_id>
service_account_email: demo-ansible@<project_id>.iam.gserviceaccount.com
credentials_file: '<path_to_credentials>n'

# Variables to be set for dynamic hosts
ansible_ssh_user: <ansible_control_user>
ansible_ssh_private_key_file: ~/.ssh/google_compute_engine
```

Environment Variables
--------------
Previously the following environment variables were exported
```
export ANSIBLE_HOSTS=ansible_hosts
export ANSIBLE_HOST_KEY_CHECKING=False
```

These are now taken care by setting the appropriate values in ansible.cfg


Demo Time
--------------
The following playbook kicks off the demo:
```
ansible-playbook google-next-demo.yml
```

This playbook cleans it up:
```
ansible-playbook cleanup.yml
```
