.. highlight:: console

.. author:: Finn <mail@f1nn.eu>

.. tag:: lang-ruby
.. tag:: web
.. tag:: audience-developers

.. sidebar:: About

  .. image:: _static/images/Ruby_On_Rails_Logo.svg
      :align: center

##########
Ruby On Rails
##########

.. tag_list::

`Ruby on rails <https://rubyonrails.org/>`_ is an open source web framework written in ruby. It follows the design paradigm *convention over configuration*. 

----

.. note:: For this guide you should be familiar with the basic concepts of

  * :manual:`Ruby <lang-ruby>` and its package manager :manual_anchor:`gem <lang-ruby.html#gem>`
  * :manual:`MySQL <database-mysql>`
  * :manual:`supervisord <daemons-supervisord>`
  * :manual:`domains <web-domains>`
  * :manual:`SSH <ssh>`

License
=======

All relevant legal information can be found here

* https://opensource.org/licenses/MIT

Prerequisites
=============

We're using :manual:`Ruby <lang-ruby>` in the stable version 2.7:

::

 [isabell@stardust ~]$ uberspace tools version use ruby 2.7
 Selected ruby version 2.7
 The new configuration is adapted immediately. Patch updates will be applied automatically.
 [isabell@stardust ~]$

::

Next we create a database:
::
 [isabell@stardust ~]$ mysql -e "CREATE DATABASE isabell_rails"
 [isabell@stardust ~]$
::

If you want to call your ruby on rails app through a domain, we add the domain as following:
::
 [isabell@stardust ~]$ uberspace web domain add isabell.example
 The webserver's configuration has been adpated.
 Now you can use the following records for your dns:
    A -> 185.26.156.55
    AAAA -> 2a00:d0c0:200:0:b9:1a:9c:37
::

Installation
============

Step 1
------
Essentialy we have to install rails itself:
::
 [isabell@stardust ~]$ gem install --user-install rails
 [isabell@stardust ~]$
::

After that, we create a new rails project with the title ``rails_project`` with the option for mysql as databse. Otherwise the default database is postgresql.
::
 [isabell@stardust ~]$ rails new rails_project --database=mysql
 [isabell@stardust ~]$
::