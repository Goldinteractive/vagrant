#GI development environment

## Intro
This is default vagrant file for the Goldinteractive development environment. It assures that everybody is developing with the same versions and in the same environment. New employees are up and running in no time.

## Vaprobash 
The installation is a copy pasted version of [Vaprobash](https://github.com/fideloper/Vaprobash). It allows us a flexible configuration and it's easy extendable for our own needs. This version will install you the following:

- sass
- compass
- grunt-cli
- bower
- php 5.3 (as used on nine, will updated if needed)
- Apache
- Mysql
- Node
- Ruby Version Manager (RVM)

## Installation
First of all you need to install [Vagrant](http://www.vagrantup.com/) which should be pretty self-explanatory. 

Next, you need to configure the Vagrant file. Change the following settings:

- `server_ip` has to be unique, .10 is reserved change it to something random between 11 and 254
- `config.vm.hostname` change it to vagrant-yourname 
- `config.vm.synced_folder` replace `~/Development/www` with the path on your system where all your webprojects are located. This folder will be automatically synced to /var/www later

Last but not least, `cd` in the folder where the Vagrantfile is located an run `vagrant up`. This will take a few minutes and you'll have to enter your password once (for NFS). 

## Usage 
Once everything is finished, you can ssh into the VM via `vagrant ssh` (obviously from the folder where you installed your VM). Now you're ready to go.

### vhosts
You can access the VM from your browser via yourserverip.xip.io  
Per default you won't see anything. For each project you add or wan't to access create a vhost entry. This is pretty easy with the Vavprobash vhost script. From anywhere just type `sudo vhost` and you see all the possible options. For example: 

	$ sudo vhost -d /var/www/sos -s sos.192.168.33.10.xip.io
	
Now you can access the site via your browser like in the old MAMP days. If you want to get fancy and, you can also manually change the created vhost:

	$ sudo nano /etc/apache2/sites-available/sos.192.168.10.xip.io.conf
	
There you could change the `DocumentRoot` to `/var/www/sos/public/` for a laravel installation. Reload the configuration with `sudo service apache2 reload`
	