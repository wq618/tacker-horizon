========================
Team and repository tags
========================

.. image:: https://governance.openstack.org/tc/badges/tacker-horizon.svg
          :target: https://governance.openstack.org/tc/reference/tags/index.html

.. Change things from this point on

Tacker Horizon UI
=================

Horizon UI for Tacker VNF Manager

* License: Apache license
* Source: https://git.openstack.org/cgit/openstack/tacker-horizon
* Bugs: https://bugs.launchpad.net/tacker
* Tacker-horizon docs: https://docs.openstack.org/tacker-horizon/latest/

Installation
============

**Note:** The paths we are using for configuration files in these steps
are with reference to Ubuntu Operating System. The paths may vary for
other Operating Systems.

The branch_name which is used in commands, specify the branch_name
as stable/<branch> for any stable branch installation. For eg:
stable/queens, stable/pike. If unspecified the default will be
master branch.

1. Clone tacker-horizon repository.

  ::

    cd ~/
    git clone https://github.com/openstack/tacker-horizon -b <branch_name>


2. Install horizon module.

  ::

    cd tacker-horizon
    sudo python setup.py install


3. Enable tacker horizon in dashboard.

  ::

    sudo cp tacker_horizon/enabled/* \
        /opt/stack/horizon/openstack_dashboard/enabled/


4. Collect and compress static files.

  ::

    ./manage.py collectstatic --noinput
    echo yes | ./manage.py compress


5. Restart Apache server.

  ::

    sudo service apache2 restart


If your server is using Systemd instead of Upstart (e.g Ubuntu 15.10
and above), use the following command instead:

  ::

    sudo systemctl restart apache2


