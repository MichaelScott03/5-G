# Setting up open5gs and UERANSIM using vagrant

Vagrant is a tool used for building and managing virtual machine environments in a single workflow.

## Installation (linux users)
### Virtual Box
First we have to install virtual box. For installing it enter the following command


```bash
sudo apt install virtual box
```
### Vagrant installation
* First give the command
```bash 
curl -O https://releases.hashicorp.com/vagrant/2.2.9/vagrant\_2.2.9\_x86\_64.deb 
```
* Now enter the following command
```bash 
sudo apt install ./vagrant\_2.2.9\_x86\_64.deb
```

### Git cloning
Now we have to clone a github repo and we need to have access to this repo as it is private.

* Enter the command
```
bash git clone --recurse-submodules https://github.com/spg-iitd/5G-and-Beyond.git 
```
If the above command gives some error (mostly due to github authorisation)
* Enter the command 
```bash 
gh auth login
```
Enter your username and password which has been given access for installation of the github repo.

* Now enter the commands
```bash 
git submodule update --recursive 
``` 

```bash
git pull --recursive submodule
```
* Finally clone the repo using command 
```bash 
gh repo clone spg-iitd/5G-and-Beyond -- --recurse-submodules
```


### Final Installation
* For final configuration and installation open 5G-and-Beyond directory on terminal.
* Check for open5gs, UERANSIM and vagrant-box directories present in 5G-and-Beyond directory.
* Check whether these directories are non-empty.
* Now open vagrant-box directory and run command.
```bash 
vagrant up 
```
Final installation will take some time.
### Running VM
* Run the command 
```bash
 vagrant up -- provision
``` 
in vagrant-box directory to re-provision VM that has been created earlier.

* Now run 
```bash 
vagrant ssh [vm-name]
```
to finally run the machine. Here [vm-name] can be **open5gs** or **UERANSIM**.

### Additional Configurations
* Run the open5gs VM using command
```bash 
vagrant ssh open5gs
```
* Now remove the open5gs directory using command
```bash
sudo rm -r open5gs
```
* Copy LoadOpen5gs directory to open5gs directory using command
```bash
sudo cp -r LoadOpen5gs/ open5gs
```
* Go to open5gs directory using
```bash
cd open5gs
```
* Enter the command
```bash
 sudo meson build --prefix=`pwd`/install
```
* Now enter the command
```bash
sudo ninja -C build
```
* Go to build directory
```bash
cd build
```
* Now enter the command
```bash
sudo ninja install
```


