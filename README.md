remote-keygen
=============

this role is meant to simplify the generation and distribution of SSH keys where
The keys reside on one master server that will connect to a series of slaves.

Our inital use case was configuring Jenkins slaves from a master.

Requirements
------------



Role Variables
--------------

The following role variables are present
| Variable | Description | default |
|----------|-------------|---------|
| skip-on-error  | If present the script will not stop on failure to generate | False (ie: fail on error ) |


Dependencies
------------

ssh-keygen is used to generate the keys. The script will test prior to running
and will fail if the binary is not present.

Example Playbook
----------------

The follwoing is the simplest example. It has a master server, which will log
into any of the slaves. The roles are - remote-keygen/master and remote-keygen/slave

```
    - hosts: control
      roles:
         - remote-keygen/master

    - hosts: executor
      roles:
        - remote-keygen/slave
```

License
-------

BSD

Author Information
------------------

alain@chiasson.org
