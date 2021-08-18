## Ansible Playbooks Demos

1. [Create user playbook](/create-user.yml)
Creates a user without a password but with Sudo capabilities by modifying the `/etc/sudoers` file. The playbook also includes a task to create a group (defaults to `docker`) where the user added "automatigically".
The playbook expects an ssh public key to be uploaded to the server under the created user account.
Example of command to run the playbook:
    ```
    ansible-playbook create-user.yml -u root --extra-vars="user=john group=docker ssh_pk_file=~/.ssh/id_rsa.pub"
    ```

    above will:
    - create a `john`'s account if it doesn't exist
    - create a `docker` group if it doesn't exist
    - add `john` into the `docker` group
    - upload a local ssh public key located at `~/.ssh/id_rsa.pub` to the server



### Notes
The playbooks target and have been tested on ubuntu~18