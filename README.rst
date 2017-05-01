ssh
===

.. image:: https://travis-ci.org/ansible-stuff/ssh.svg?branch=master
  :target: https://travis-ci.org/ansible-stuff/ssh/builds

Ansible role for increasing the security of SSH service.

**!!! WARNING:** This script will disable SSH password authentication.
If password based authentication is only way to use SSH you will
**not be able to connect** to remote machine anymore **!!!**

Run Playbook
------------

Clone this repository:

.. code-block:: none

  > git clone https://github.com/ansible-stuff/ssh
  > cd ssh
  [ssh]>

Copy inventory sample from ``sample/hosts`` and fill it with information about
your remote:

.. code-block:: none

  [ssh]> cp sample/hosts hosts
  [ssh]> vim hosts

Run playbook:

.. code-block:: none

  [ssh]> ansible-playbook --inventory-file hosts role.yml

Integrate Playbook
------------------

`Ansible Galaxy <https://galaxy.ansible.com/ansible-stuff/ssh/>`__
can help you to integrate this role into your project.

Create ``requirements.txt`` file with content:

.. code-block:: none

  ansible-stuff.ssh,v1.0

Add custom path for externally downloaded roles to ``ansible.cfg``:

.. code-block:: none

  [defaults]
  roles_path=_3rdParty/roles

Install dependencies:

.. code-block:: none

  > ansible-galaxy install -r requirements.txt -p _3rdParty/roles

Here is a playbook example ``ssh.yml``:

.. code-block:: yaml

  ---
  - hosts: ssh
    roles:
      - role: ansible-stuff.ssh

And inventory example ``hosts``:

.. code-block:: none

  [ssh]
  my-machine.example.com:12345 ansible_user=root

Run playbook:

.. code-block:: none

  > ansible-playbook --inventory-file hosts ssh.yml

License
-------

`BSD <https://github.com/ansible-stuff/ssh/blob/master/LICENSE>`__

Author Information
------------------

Ruslan Baratov <ruslan_baratov@yahoo.com>
