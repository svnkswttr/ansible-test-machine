# ansible-test-machine
How I made my laptop an ansible all-in-one machine

# Install ansible tower
1.) Make yourself a RedHat developer account (free)

2.) Install RHEL8 GUI-Server on your machine

3.) Install a few prereqs: yum -y install wget tar

4.) download Ansible Tower (bundled installer) from here: https://releases.ansible.com/ansible-tower/setup-bundle/
    cd /opt && wget https://releases.ansible.com/ansible-tower/setup-bundle/ansible-tower-setup-bundle-3.8.6-2.tar.gz

5.) extract the installer: tar xfv ansible-tower-setup-bundle-3.8.6-2.tar.gz && cd ansible-tower-setup-bundle-3.8.6-2

6.) edit the inventory file and enter a password for the admin_passowrd and the pg_password

7.) start the install by using the setup.sh

8.) wait for completion

# Install GitLab (https://computingforgeeks.com/how-to-install-and-configure-gitlab-on-centos-rhel/)

1.) install prereqs:
    sudo yum -y update && sudo yum -y install curl vim policycoreutils python3-policycoreutils postfix
    sudo systemctl enable --now postfix

2.) curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash

3.) sudo yum install gitlab-ce

4.) sudo vi /etc/gitlab/gitlab.rb:
    add your DNS name and desiered port (to have no conflicht on 80 where tower runs) 
    external_url 'http://localhost:8888'
5.) apply the config: sudo gitlab-ctl reconfigure
6.) wait
7.) get the initial root password for gitlab by sudo cat /etc/gitlab/initial_root_password 

Now set up your gitlab as needed. Do the same for tower.

Optionally you can install VirtualBox and Hashicorp vagrant on the machine as well. 
So you will have an environment that is rebuilt easyly.
