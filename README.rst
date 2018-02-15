==========================
Share&Charge Documentation
==========================

This is the official guide for the Share&Charge open network and components.

Building this documentation
===========================

This project uses:

* Python3
* Pipenv_ as packaging tool to manage virtual environments and requirements

.. _Pipenv: http://docs.pipenv.org/en/latest/

**Install or update** Pipenv to your system::

   pip3 install -U pip pipenv

From inside the root folder, **activate your virtualenv shell**::

   pipenv shell

Install **dependencies**::

   pipenv install

From the ``docs`` folder, build the HTML and open the index page::

   cd docs/
   make html
   open _build/html/index.html
