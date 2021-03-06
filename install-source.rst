Install from source (generic)
*****************************

1. Install Zammad on your system
================================

You can directly download Zammad from https://ftp.zammad.com/ or use the direct url to get the latest stable release via https://ftp.zammad.com/zammad-latest.tar.gz

::

 root@shell> wget https://ftp.zammad.com/zammad-latest.tar.gz
 root@shell> cd /opt/
 root@shell> mkdir zammad
 root@shell> tar -xzf zammad-latest.tar.gz -C zammad
 root@shell> useradd zammad
 root@shell> su - zammad


2. Install all dependencies
===========================

::

 zammad@shell> cd zammad
 zammad@shell> gem install bundler

For PostgreSQL (note, the option says "without ... mysql")
----------------------------------------------------------

::
 
 zammad@shell> bundle install --without test development mysql

For MySQL (note, the option says "without ... postgres")
--------------------------------------------------------

::

 zammad@shell> bundle install --without test development postgres


3. Configure your databases
===========================

::

 zammad@shell> cp config/database.yml.dist config/database.yml
 zammad@shell> vi config/database.yml


4. Initialize your database
===========================

::

 zammad@shell> export RAILS_ENV=production
 zammad@shell> export RAILS_SERVE_STATIC_FILES=true # only if you use no http reverse proxy
 zammad@shell> rake db:create
 zammad@shell> rake db:migrate
 zammad@shell> rake db:seed


5. Change directory to zammad (if needed) and start the web server:
===================================================================

::

 zammad@shell> rake assets:precompile
 zammad@shell> rails s -p 3000 # application web server
 zammad@shell> script/websocket-server.rb start # non blocking websocket server
 zammad@shell> script/scheduler.rb start # generate overviews on demand, just send changed data to browser


6. Go to http://localhost:3000 and you'll see:
==============================================

* "Welcome to Zammad!", there you need to create your admin user and you need to invite other agents.
