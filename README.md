

Installing Ansible Tower
------------------------
The reference topology by default only gives 1G of RAM to the `oob-mgmt-server`.
You will need to increase the RAM for the `oob-mgmt-server` to 2G in order for
Ansible Tower to install.

    git clone https://github.com/cumulusnetworks/cldemo-vagrant
    # edit Vagrantfile and replace v.memory for the oob-mgmt-server from 1024 to 2048
    vagrant up oob-mgmt-server oob-mgmt-switch leaf01 leaf02
    vagrant ssh oob-mgmt-server
    sudo su - cumulus
    sudo apt-get install software-properties-common
    sudo apt-add-repository ppa:ansible/ansible
    sudo apt-get update
    sudo apt-get install ansible
    wget https://releases.ansible.com/awx/setup/ansible-tower-setup-latest.tar.gz
    tar xvzf ansible-tower-setup-latest.tar.gz
    cd ansible-tower-setup-*
    ./configure
    localhost
    i
    vagrant
    vagrant
    y
    sudo ./setup.sh
    git clone https://github.com/cumulusnetworks/cldemo-ansible-tower

*In a new terminal*

    ssh -L 9000:localhost:443 vagrant@localhost -p 2222 -o StrictHostKeyChecking=no
    vagrant

Leave this terminal open for the duration of the demo - this creates an SSH
tunnel that will allow you to use the Ansible website from your host machine.
In Firefox or Chrome, navigate to https://localhost:9000 - you will receive an
error message stating that your connection is not secure. Go to Advanced and
either add an exception or tell it to proceed to localhost anyway.

Your username is `admin` and your password is `vagrant`

When it asks for a license file, copy and paste your license file from
Red Hat in the box. If you don't have a license, click on the button to
receive a free trial license that can be used for evaluation purposes or in
installations of up to 10 nodes (which is sufficient for these demo purposes).


Setting up the Inventory
------------------------
Your inventory.

    cd ~/cldemo-ansible-tower
    sudo tower-manage inventory_import --source=. --inventory-name="Reference Topology"
