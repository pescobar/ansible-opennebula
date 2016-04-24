Ansible playbooks to deploy a basic open nebula setup based on "Quickstart: OpenNebula on CentOS 7 and KVM" in [OpenNebula 4.14 docs] (http://docs.opennebula.org/pdf/4.14/opennebula_4.14_design_and_installation_guide.pdf)

This is not ready for a production deployment. It will use sqlite and won't setup nfs so it only supports deploying both the master and kvm client in the same node. By now it's only useful to do a test deployment of OpenNebula running all services in the same physical machine. This playbook asumes the network interface used by opennebula is the same interface used to connect/deploy with ansible. 

Tested only in Centos 7.2


## Usage

Edit file `hosts` to add your machine hostname and then deploy both playbooks in the same machine

`ansible-playbook -i hosts opennebula-master.yml`

`ansible-playbook -i hosts opennebula-kvm-node.yml`


Once all playbooks have finished correctly you should be able to connect to `http://open-nebula-machine:9869/`. You can find the webui user/pass in `~oneadmin/.one/one_auth`. This user and password is automatically generated during installation.

Now you can follow the section `2.1.4 Step 3. Basic Usage` in the documentation to add a kvm-host (which will be localhost) and virtual resources and then boot your first virtual machine.

