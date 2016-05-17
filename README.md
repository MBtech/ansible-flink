# ansible-flink
An Ansible way to deploy Apache Flink.

Edit the hosts_sample to add the hostnames or IP of your nodes
Setup Flink using  
`$ ansible-playbook -i hosts_sample roles/configure.yaml`

Run Flink using  
`$ ansible-playbook -i hosts_sample roles/run_flink.yaml`

Stop Flink using  
`$ ansible-playbook -i hosts_sample roles/stop_flink.yaml`

Download and configure Hadoop using
`$ ansible-playbook -i hosts_sample roles/configure-hadoop.yaml`

You will need to modify the variables specified in the `ansible-flink/group_vars/all/vars.yaml` file. There are two variable defined there:

 1. `base_path`: is the directory name where flink will be
    downloaded and setup
 2. `user_name`: is the user name that you have on the remote machines.

>  **If `/home` is mounted on NFS**
>  If you have a home directory `/home`mounted on a NFS. The root user might not be able to access that directory. Since by default ansible creates `.ansible` directory in`/home/username`, might run into some troubles for the commands that require sudo.  In order to avoid this problem you will need to direct ansible to create the .ansbile directory in a place that is accessible by the root user, perhaps `/tmp`.  Change the path for `.ansible` in `ansible_sample.cfg` and then
>`$ cp ansible_sample.cfg ansible.cfg`
