Install on Ubuntu via DEB
*************************

Currently we support Ubuntu 16.04


Add Zammad DEB Repo and install
===============================

::

 wget -qO - https://deb.packager.io/key | sudo apt-key add -
 echo "deb https://deb.packager.io/gh/zammad/zammad xenial stable" | sudo tee /etc/apt/sources.list.d/zammad.list
 sudo apt-get update
 sudo apt-get install zammad


Go to http://localhost and you'll see:
======================================

* "Welcome to Zammad!", there you need to create your admin user and you need to invite other agents.


You can manage the Zammad services manually:
============================================

Zammad
------

::

 sudo systemctl status zammad
 sudo systemctl stop zammad
 sudo systemctl start zammad
 sudo systemctl restart zammad

Only web application server
---------------------------

::

 sudo systemctl status zammad-web
 sudo systemctl stop zammad-web
 sudo systemctl start zammad-web
 sudo systemctl restart zammad-web

Only worker process
-------------------

::

 sudo systemctl status zammad-worker
 sudo systemctl stop zammad-worker
 sudo systemctl start zammad-worker
 sudo systemctl restart zammad-worker

Only websocket server
---------------------

::

 sudo systemctl status zammad-websocket
 sudo systemctl stop zammad-websocket
 sudo systemctl start zammad-websocket
 sudo systemctl restart zammad-websocket


