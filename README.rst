==========================
Share&Charge Documentation
==========================

This is the official guide for the Share&Charge open network and components.

http://sharecharge-documentation.readthedocs.io/en/latest/

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

Troubleshooting:

If you have ubuntu16, it comes with python3.5. Here's how to upgrade it to 3.6

   sudo add-apt-repository ppa:jonathonf/python-3.6
   sudo apt-get update
   sudo apt-get install python3.6
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.5 1
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 2
   sudo update-alternatives --config python3
   python3 -V
