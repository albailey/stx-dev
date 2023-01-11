Step 1: Download and install VirtualBox

Step 2: Download and install vagrant

Step 3: Update defaults.yaml or create a custom.yaml with the overridden values
  
Step 4: vagrant up

Supported Capabilities:

 - Disk:
   - support bigger VBOX disk (default is 500 G)
   - support relocate the DISK to be on an SSD (in case vbox is setting up VM disks on a non SSD drive)
   - support disk resize within the VM (otherwise it will use the default 20G disk from the base image)
   
 - User:
   - support ssh as the new user.
   - setup bash env (variables)
  
 - Build:
   - repo init
   - repo sync
   - setup git settings
   - creates required directories for build env
   - minikube setup
   - support restart of minikube on reboot
   - update containers (apt-get update) prior to running the downloader
   - invoke downloader
   
  - Alternative manifest support
   - support setting up another manifest (ALT_PORT / ALT_HOST / SSH_URL) to allow creating an alternative manifest (this is not needed if just building the normal STX)
 
Setup Timing Results (based on my dev machine and network)
   - 3 minutes to download and provision the Debian VM
   - 6 minutes to clone the source code.
   - 7 minutes initialize the build containers
   - 9 minutes to run the downloader for the STX build packages
   - Total: 25 minutes

Build Timing:
   stx shell "time build-pkgs"   takes approximately 10 hours

Future Items:
 - populate the initial mirror from previous upstream builds
 - Provide additional git ssh-key setup (for git review, etc..)
 - DHCP support (so you can connect to the VM by its name)
    - verified /etc/machine-id is unique, so DHCP should work for these VMs.
 - NIS (home dir) support
 - X11 ssh support
