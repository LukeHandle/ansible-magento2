# ansible

I have no idea what I'm doing.

## Method 1: From your local machine, provision a VM

This uses VirtualBox + Vagrant with the `ansible_local` provisioner.

Note: This method creates a VM with an IP address of `192.168.33.10`.  You will need to check that this does not conflict on your network.  Adjust `config.vm.network` in `Vagrantfile` if necessary.

Install `vagrant` and `virtualbox`, then:
```
$ git clone https://github.com/josephchapman/ansible.git

$ cd ansible

$ vagrant up
```

## Method 2: Directly on a server

This method uses `ansible` locally.

Install `ansible`, then:
```
# git clone https://github.com/josephchapman/ansible.git

# ansible-playbook -i "localhost," -c local ansible/provisioning/site.yml
```