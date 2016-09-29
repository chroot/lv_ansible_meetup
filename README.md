Execute the commands on everything in the inventory file
<pre>ansible -i inventory -a "free -m" all</pre>

Using the group name defined in the inventory
<pre>ansible -i inventory -a "free -m" lamp</pre>

View VM specifics
<pre>ansible -i inventory -m setup all </pre>

Test communications with VM(s)
<pre>ansible -i inventory -m ping all</pre>

View VM specifics using the group name
<pre>ansible -i inventory -m setup lamp</pre>

Test communications with VM(s) in the lamp group
<pre>ansible -i inventory -m ping lamp</pre>
