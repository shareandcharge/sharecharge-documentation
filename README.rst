==========================
Share&Charge Documentation
==========================

This is the official guide for the Share&Charge open EV charging network and components.

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

From the ``docs`` folder, build the HTML::

    cd docs/
    make html

Open the index page on MacOS::

    open _build/html/index.html

Or on a Linux distribution::

    firefox _build/html/index.html

Alternatively, if you want to create a PDF::

    make latexpdf
    open _build/latex/ShareChargeDocumentation.pdf

Troubleshooting
===============

If you have Ubuntu 16.04, it comes with Python3.5. Here's how to upgrade it to 3.7::

   sudo add-apt-repository ppa:jonathonf/python-3.6
   sudo apt-get update
   sudo apt-get install python3.6
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.5 1
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.7 2
   sudo update-alternatives --config python3
   python3 -V
