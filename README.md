# vagrant-devstack

This Vagrantfile provision a single OpenStack appliance to homelab tests.  

The execution is straighforward:

## Prerequisites:

- VirtualBox
- Vagrant
- [vagrant-disksize](https://github.com/sprotheroe/vagrant-disksize) plugin
- 2 CPU Cores, 8 GB RAM Memory and 60 GB hard drive space as minimum.

## Installing:

- Clone this repo

```bash
$ git clone https://github.com/enmanuelmoreira/vagrant-devstack
```

- Change to vagrant-devstack directory:

```bash
$ cd vagrant-devstack
```

- Open the **initial-devstack-setup.sh** file with your favorite text editor, and you must change these values:

  - **ADMIN_PASSWORD=admin** (change to you own password)
  - **FLOATING_RANGE=192.168.0.0/24** (change to your CIDR network)

- Open the **Vagrantfile** file, and you must be change these values:
  - **config.disksize.size = "70GB"** (you can change to an upper value)
  - **v.memory = 10240** (adjust to desired memory size)
  - **v.cpus = 8** (adjust to desired CPU size)

- Execute the Vagrant Command:

```bash
$ vagrant up
```

After the VM has been up and running, you must be to login into the VM:

```bash
$ vagrant ssh
```

- Change to root user and then to the stack user:

```bash
$ sudo su
$ su - stack
```

- Let's discover the assigned IP address of the VM:

```bash
$ ip a
```

- Copy the IP Address of the VM and let's modify the local.conf file located on devstack directory:

```bash
$ cd devstack
$ sudo vi local.conf
```

Paste the IP Address on the **HOST_IP=** parameter, it should be looks like this:

```plaintext
HOST_IP=192.168.0.134
```

Save the changes and close the local.conf file.

- Run the script stack.sh script:

```plaintext
$ ./stack.sh
```

It's takes 45 minutes to 1 hour to provisioning the OpenStack platform.

You can login to the OpenStack platform on your web browser with the configured IP address:

http://192.168.0.134/

To access to the OpenStack Dashboard:

http://192.168.0.134/dashboard
