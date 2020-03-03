I don't know but it works somehow for some reason and 
that is the case here haha

sudo apt-get update 
sudo apt-get install vim

if this returns an error
do the following:
	Press> alt+f2
	Type> 'software-properties-gtk'
	And check all the boxs
Now try again:
- install pip3 on ubuntu:
	- `apt-get install python3-pip`
####Install Anacodna on Ubuntu
	- cd /tmp
	-Dowload the file using curl:
	-> curl -O https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh
	-Verify data integrity using sha256
	->sha256sum Anaconda3-2019.03-Linux-x86_64.sh
	-Go to [Anconda with Python 3](https://docs.anaconda.com/anaconda/install/hashes/lin-3-64/)Check the output of the above sha256 code match with the anacodna version we have installed (in this case Anacodna3-2019-03-Linux86_64.sh), it should match
	-Now run the bash script
	-> bash Anaconda3-2019.03-Linux-x6_64.sh
	-> we should see welcome of python
	-> Press enter to continue and write Yes to accepte and choose (or accept the default locaion) for instalation.
	-> Type yes so that you can use the conda command. 
	-> You can now activate the installation by sourcing the ~/.bashrc file:
	--> source ~/.bashrc
	-> Verify conda is installed using `conda list` command
### Setting Up Anaconda Environments
	- check to see which versions of Python are available for us to use:
	-> `conda search "^python$"`
	-Let’s create an environment using the most recent version of Python 3. We can achieve this by assigning version 3 to the python argument. Let us call the environment as python3_env
	-> `conda create --name python3_env python=3`
	--> To target a more specific version of Python we can use eg. 'conda create -n my_env35 python=3.5`
	-> Check if the new environment is created: `conda-env list`
	->activate your new environment by typing the following:
	-->`conda activate python3_env`
	--> `python --version` to check the version of py
	->`conda deactivate` deactivates the environment
	-> To add additional packages, such as numpy:
	-->`conda install --name my_env35 numpy`
	-> To remove the environmnet that you will no longer need it
	-->`conda remove --name my_env35 --all`
	- To update unaconda `conda update conda`
	- To uninstall anaconda `conda install anaconda-clean` and type `y` this will remove configuration files for when you uninstall Anaconda.
	-> `anaconda-clean --yes` will clean(removes the file and creates .anaconda_backup in your home directory
	-> you can now remove your entrie Anacodna directory by entering `rm -rf ~/anaconda3` 
	-> Finally you can remove the PAH line from your `.bashrc` file that anaconda added. To do so, first open a text editor
	--> `vim ~/.bashrc` scroll down till uo see @ added by Anaconda and remove the export line

### Generate public and private key ubuntu
- Step 1 — Create the RSA Key Pair
	-> `ssh-keygen` You press enter for all and keep the deafult
	-> CD to home directory `cd` enter
	-> ls -a should give you the `.ssh` directory.
	-> you can `cd .ssh` to see the private and public key files.
	-> pbcopy < id_rsa.pub` will copy the public key to clipboard.
	- **Note** If pbcopy is not installed follow the following steps
	-> `sudo apt-get install xclip -y`
	-> 'vim ~/.bashrc' and add the following two alias at the end of the linefor pbcopy command to work
	--> 'alias pbcopy='xclip -selection clipboard'
	--> 'alias pbpaste='xclip -selection clipboard -o'
	-> Save and exit and now refresh the bash to import the new setting using
	--> `source ~/.bashrc`
 - Step 2 Copy the Public Key to Ubuntu Server
	-> we can use `ssh-copy-id` command:
	--> `ssh-copy-id username@remote_server`
	-> If `ssh-copy-id` is not available, we can use ssh. First use cat command to read contentes of pblic SSH key on our computer. Then pip that through SSH conncetion to the remote server
	-->`cat ~/.ssh/id_rsa.pub | ssh username@remote_host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"`
