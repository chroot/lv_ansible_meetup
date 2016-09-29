# Second Task -
1. Create a playbook that will install the required software packages for our LAMP stack
  * epel-release
  * firewalld
  * httpd
  * mod_ssl
  * mariadb-server
  * wordpress
2. To install wordpress you will need to ensure that `epel-release` is installed first.
3. Start the services and ensure they sustain a reboot
4. Configure Firewalld
5. Wordpress installs to `/usr/local/wordpress` so you'll need to create a symbolic link to `/var/www/html/wordpress`
6. Database – Skip it for now; our goal is deploy a solid stack
Using the following link as a reference, you could create the wordpress database; I would skip this at this time and perform this manually.  This is purely based on time -

# References -
* [Ansible Yum Module](http://docs.ansible.com/ansible/yum_module.html)
* [Ansible Service Module](http://docs.ansible.com/ansible/service_module.html)
* [Ansible FirewallD Module](http://docs.ansible.com/ansible/firewalld_module.html)
* [Ansible File Module](http://docs.ansible.com/ansible/file_module.html)
* [Ansible MysqlD Module](http://docs.ansible.com/ansible/list_of_database_modules.html#mysql)

# Example files
<pre>git checkout task2</pre>
