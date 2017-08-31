remote-keygen
=============

this role is meant to simplify the generation and distribution of SSH keys where
The keys reside on one master server that will connect to a series of slaves.

My initial use case was configuring Jenkins slaves from a master.

Requirements
------------

None. 

Role Variables
--------------

The following role variables are present
| Variable | Description | default |
|----------|-------------|---------|
| keymaster  | The keymaster variable must have master host in the master/slave relationship. The name is based on Ansible server names. | localhost |

WARNING: Define this value. there is a defect that makes this not work as expected since localhost is not a Ansible server.

The key server MUST be defined before the slaves.

Dependencies
------------

ssh-keygen is used to generate the keys. The script will test prior to running
and will fail if the binary is not present.

Example Playbook
----------------

The following is the simplest example. It has a master server, which will log
into any of the slaves. If the current server is the keymaster, a keyfile will be generated
and distributed to all servers.

```
    - hosts: control
      roles:
        - { role: remote-keygen, keymaster: 'control' }

    - hosts: executor
      roles:
        - { role: remote-keygen, keymaster: 'control' }
```

License
-------

BSD

Author Information
------------------

alain@chiasson.org
