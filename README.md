# First Task -
1. Create an inventory file and list your VM.
  * In my example I have `node1.example.com`
2. Place the VM in an inventory group named `lamp`
3. Add attributes about this VM, these will be used because we don't have DNS and you may not be using your local account
3. Using this inventory file test some ad-hoc commands
  * Test communications with all VMs
  <pre>ansible -i inventory -m ping all</pre>
  * Check memory on all VMs
  <pre>ansible -i inventory -a "free -m" all</pre>
  * Check memory for just the `lamp` servers
  <pre>ansible -i inventory -a "free -m" lamp</pre>
  * View the VM Specific information using the `lamp` group and without
  <pre>ansible -i inventory -m setup all </pre>
4. Review that beautiful beautiful info you just got

# References -
* [Ansible Ad-Hoc Intro](http://docs.ansible.com/ansible/intro_adhoc.html)
* [Ansible Running Ad Hoc Commands](http://ansible-tips-and-tricks.readthedocs.io/en/latest/ansible/commands/)

# Example files
<pre>git checkout task1</pre>
