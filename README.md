SSH Port Fingerprint
=========

This role will detect the SSH port to determine if it is standard or custom and change it if required.
It will also scan the host key fingerprints and prompt to add them to the known hosts.

This role will record the following SSH Host Keys by default (RSA, DSA, ECDSA, ED25519).
Open an issue to support new/additional formats.

Known hosts will be put in a `known_hosts.d` directory with a file per host (`inventory_hostname`) for easy separation.
Normal `known_hosts` locations will continue to work as expected.

Requirements
------------

This requires the `dig` command on the Ansible host.

Role Variables
--------------

ssh_port_change: false    # Specify true if you want this role to update the SSH listening port to the specified ansible_port.
ansible_port: 22          # Specify which port SSH "should" be listening on.
global_known_hosts: false # Specify true to add to the global known_hosts, or default to the Ansible calling user's known_hosts.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Please note that `gather_facts` is set to disable, you shouldn't be able to gather facts until after we configure the fingerprint, the role will run the setup module afterwards.

```yaml
---
- name: Playbook Name
  hosts: MyHosts
  become: true
  gather_facts: false
  
  roles:
    - role: notmycloud.ssh_port_fingerprint
      vars:
        ssh_port_change: false    # Specify true if you want this role to update the SSH listening port to the specified ansible_port.
        ansible_port: 22          # Specify which port SSH "should" be listening on.
```

License
-------

MIT License

Copyright (c) 2022 Not My Cloud <devops@notmy.cloud>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Author Information
------------------

Coming Soon!

Support
------------------

For support, please raise an issue and provide the following items.
Do not reach out directly for support, all requests will be ignored.

- Sample task/playbook to replicate your issue.
- Ansible version `ansible --version`
- Ansible config `ansible-config dump --only-changed -t all`, if using an older version of Ansible, omit the `-t all`.
- Description of what is happening vs what you expect to happen.
