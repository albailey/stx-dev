Step 1: Download and install VirtualBox
Step 2: Download and install vagrant
Step 3: Update defaults.yaml or create a custom.yaml with the overridden values
  Note: edit the Vagrantfile "config.vm.define" value so that you can 'vagrant up' more than one VM
Step 4: vagrant up

Supported Capabilities:
 Disk:
  - support bigger VBOX disk
  - support relocate the DISK to be on an SSD
  - support disk resize within the VM
 User:
  - support ssh as the new user.
  - setup bash env (variables)
 Build:
  - repo init
  - repo sync
  - setup git settings
  - creates required directories for build env
  - minikube setup
  - update containers prior to running the downloader
  - invoke downloader
  - support restart of minikube on reboot
 
Current timing (approximately 25 min):
   - 3 minutes to download and provision the Debian VM
   - 6 minutes to clone the source code.
   - 7 minutes initialize the build containers
   - 9 minutes to run the downloader for the STX build packages

Future Items:
 - populate the initial mirror from previous upstream builds
 - provide data on how to upload the git certs (for git review, etc..)
 - DHCP support (so you can connect to the VM by its name)
    verified /etc/machine-id is unique, so DHCP should work for these VMs.
 - NIS (home dir) support

