Vagrant is a tool by Hashicorp that is used to deploy virtual machines on your local environment from a declarative build file. 

#### Install
https://www.vagrantup.com/downloads

``` Ubuntu/Debian
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -

sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

sudo apt-get update && sudo apt-get install vagrant
```

``` CentOS/RHEL
sudo yum install -y yum-utils

sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo

sudo yum -y install vagrant
```

#### Check Version
```
vagrant version
```

#### Configuring a VM
You can start a VM using the default settings of the box by using:
```
vagrant init centos/7
```
This will create a Vagrantfile in your current directory with the settings for this VM.

To see other images check: https://app.vagrantup.com/boxes/search

It can sometimes be worth it to find a box hosted on another mirror because the download speed can be very slow.

#### Starting a VM
```
vagrant up
```

#### Connect to a VM
```
vagrant ssh
```

#### Stopping a VM
```
vagrant halt
```

#### Delete a VM
```
vagrant destroy
```

#### Reload a VM
If you change the Vagrantfile configuration you will need to reload the VM
```
vagrant reload
```

#### Snapshot a VM
Before you make changes to a VM it is a good idea to take a snapshot before hand in case the change causes an issue. 
```
vagrant snapshot save <name_of_snapshot>
```
Without specifying it, the system will infer the default vm, otherwise it needs to be specified before the <name_of_snapshot>.

#### Restore a snapshot
```
vagrant snapshot restore <name_of_snapshot> 
```

#### Delete a snapshot
```
vagrant snapshot delete <name_of_snapshot>
```

#### Configuring a VM
If you edit the Vagrantfile you change the settings of the VM

```
 config.vm.provider "virtualbox" do |vb|
   vb.memory = "1024"
   vb.cpus = 2
   vb.name = "my_centos_vm"
 end
```