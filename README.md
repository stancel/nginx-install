nginx_install
=========

Ansible role to install the open source version of NginX and copies over a customized main nginx.conf configuration file. This role does not add the virtual hosts/server blocks needed for any websites that will run on the webserver. Separate roles, stancel.nginx_site_setup and stancel.nginx_site_removal, cover the adding or removal of any virtual hosts.

Requirements
------------

An Ubuntu or Debian based distribution. 

Role Variables
--------------

Will the webserver host more than one website? This determines where to place the logs. The default is false.
```
	nginx_install_shared_webserver: false
```

The non-root linux user that NginX will run as. The default is "www-data".
```
	nginx_install_nginx_user: "www-data"
```

The number of NGINX worker processes (the default is auto)
```
	nginx_install_nginx_worker_processes: auto
```

The maximum number of connections that each worker process can handle simultaneously.
```
	nginx_install_nginx_worker_connections: 1024
```

Choose to install NginX from their official repository or to use the OS repository. Options are "nginx_repository" or "os_repository". Default is nginx_repository.

```
	nginx_install_nginx_install_from: nginx_repository
```

Specify which branch of NGINX Open Source you want to install. Options are 'mainline' or 'stable'. Only works if 'nginx_install_nginx_install_from' is set to 'nginx_repository'. Default is stable.

```
	nginx_install_nginx_branch: stable
```


Dependencies
------------

None.

Example Playbook
----------------

Copy and edit *defaults/main.yml* to your *vars/main.yml*

	- hosts: your_webserver
	  vars_files:
	    - vars/main.yml
	  roles:
	    - stancel.nginx_install


or just pass the variables in the playbook


	- hosts: your_webserver 
	  vars:
		nginx_install_shared_webserver: false
		nginx_install_nginx_user: "www-data"
	  roles:
	    - stancel.nginx_install

License
-------

GPLv3

Author Information
------------------

[Brad Stancel](https://github.com/stancel) 

