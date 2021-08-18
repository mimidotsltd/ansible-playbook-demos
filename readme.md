## Ansible Playbooks Demos

1. [Create user playbook](/create-user.yml)
Creates a user without a password but with Sudo capabilities by modifying the `/etc/sudoers` file. The playbook also includes a task to create a group (defaults to `docker`) where the user added "automatigically".
The playbook expects an ssh public key to be uploaded to the server under the created user account.
Example of command to run the playbook:
    ```sh
    ansible-playbook create-user.yml -u root --extra-vars="user=john group=docker ssh_pk_file=~/.ssh/id_rsa.pub"
    ```

    above will:
    - create a `john`'s account if it doesn't exist
    - create a `docker` group if it doesn't exist
    - add `john` into the `docker` group
    - upload a local ssh public key located at `~/.ssh/id_rsa.pub` to the server

2. [Install Docker && Docker compose](/install-docker.yml)
The playbook includes tasks to install docker, docker-compose,
 and create a group (_defaults to docker_) that will own docker-compose executable.

 Example command to run the playbook:

   ```sh
    ansible-playbook install-docker.yml -u root --extra-vars="group=docker"
   ```



### Notes
- The playbooks have been tested only on ubuntu~18
- The playbooks targets `all` hosts by default