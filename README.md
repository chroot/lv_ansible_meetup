# Third Task -
1. Break the tasks into roles
 * security
 * apache
 * mariadb
2. These to start will be very sparse but our primary objective here is
 * start using all those facts we got from `-m setup` in our files
 * start using variables
 * start using dependencies
3. Build out the roles directory structure using the best practices guides
<pre> mkdir roles
cd roles
for i in security apache mariadb wordpress; do
   ansible-galaxy init ${i}
   done</pre>
4. Start with the Apache role and transfer your tasks from the previous steps
    to here

        roles/                     # < -- parent directory for roles
        apache/                   #       this hierarchy represents a "role" for apache
          tasks/                  #
                main.yml          #  <-- Where our tasks will live
          handlers/               #
                  main.yml        #  <-- When we use notify for restarts it
                                  #      calls from here
          templates/              #  
                wordpress.conf.j2 #  <--- Our wordpress.conf that will use facts
          files/                  #
                httpd.conf        #  <-- Copy our default httpd.conf
          vars/                   #
              main.yml            #  <-- ServerAlias variable defined here
          meta/                   #
              main.yml            #  <-- define mariadb as a role dependency here

 * You can use the example_* files.  These are files that work on the end system.
   From there back your way into the facts.
 * templates /
    * Change the `example_wordpress.conf` file as follows
      * `VirtualHost 192.168.86.246:80` should fill with your systems IP address
      * `ServerName`, `ErrorLog` and `CustomLog` should fill with your servers name
      * `ServerAlias` should fill from the var `MyServerAlias` you'll define a bit later
  * files /
    * deploy the `httpd.conf` file, ensuring it's permissions when delivered
  * handlers /
    * Create a handler for the `httpd` service so when these changes are made we restart the service
  * vars /
    * define the `MyServerAlias` variable as `www.example.com` to be populated in the `wordpress.conf`
  * meta /
    * define mariadb as a role dependency but leave it commented out so you can test without that role

5. Build out the `mariadb` role

        roles/                     # < -- parent directory for roles
        mariadb/                  # this hierarchy represents a "role" for apache
          tasks/                  #
                main.yml          #  <-- Where our tasks will live
          handlers/               #
                  main.yml        #  <-- When we use notify for restarts it calls from here
          templates/              #  
                my.cnf.j2         #  <--- an easy mysql config that uses a
                                  #       variable from default for port
          defaults                #
              main.yml            #  <-- Define the mariadb port here
          meta/                   #
              main.yml            #  <-- define mariadb as a role dependency here

 * You can use the example_* files as needed.
  * templates /
    * Change the `my.cnf.j2` to use `MyDefaultMariaDBPort` for it's port
  * handlers /
    * Define a mariadb service restart here to be used after the my.cnf is deployed
  * defaults /
      * set the `MyDefaultMariaDBPort` variable here
  * tasks /
      * Install `mariadb-server` and deliver the `my.cnf` file; finally restart `mariadb`

# References -
* [Ansible Template Files](http://docs.ansible.com/ansible/template_module.html)
* [Ansible Handlers](http://docs.ansible.com/ansible/glossary.html)
* [Ansible Notifications](http://docs.ansible.com/ansible/list_of_notification_modules.html)

# Example files
<pre>git checkout task3</pre>
