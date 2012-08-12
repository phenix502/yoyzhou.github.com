---
layout: post
title: "Install Python Setuptools/Distribute for Python2 and Python3"
date: 2012-08-12 20:23
comments: true
categories: [Python, Distribute, Setuptools]
---

Since [Setuptools](http://pypi.python.org/pypi/setuptools/) doesn't support Python3.\* so far, for Python3.\* we choose [Distribute](http://pypi.python.org/pypi/distribute/), _**it is a fork of the Setuptools project.**_

{% blockquote @PyPI Distribute http://pypi.python.org/pypi/distribute/#disclaimers%}
Distribute is intended to replace Setuptools as the standard method for working with Python module distributions.
{% endblockquote %}

##Install python Setuptools with easy_install for Python2.*  

1 Download setuptools from http://pypi.python.org/pypi/setuptools/, select the appropriate OS/version you want.
{% codeblock  Install Setuptools(v2.7) install_setuptools.sh%}
sudo sh Downloads/setuptools-0.6c11-py2.7.egg

{% endcodeblock%}
Output:
{% codeblock  Output install_setuptools.sh%}
Processing setuptools-0.6c11-py2.7.egg
Copying setuptools-0.6c11-py2.7.egg to /usr/local/lib/python2.7/dist-packages
Adding setuptools 0.6c11 to easy-install.pth file
Installing easy_install script to /usr/local/bin
Installing easy_install-2.7 script to /usr/local/bin
{% endcodeblock%}


##Install python Distribute with easy_install for Python3.*
{% codeblock  Install Distribute install_distribute.sh%}
curl -O http://python-distribute.org/distribute_setup.py
sudo <python-cmd> distribute_setup.py
{% endcodeblock%}
Output:
{% codeblock  Output install_distribute.sh%}
Adding distribute 0.6.28 to easy-install.pth file
Installing easy_install script to /usr/local/bin
Installing easy_install-3.2 script to /usr/local/bin
{% endcodeblock%}
**Note:** Make sure \<python-cmd\> is a python3.* command, in my PC, Python2.* command is python, while the Python3.* command is python3,  use \<python-cmd\> --version to check out version of \<python-cmd\>. 


Now per installing 2.* package, using:
{% codeblock Install 2.* Package install_package2.sh%}
easy_install-2.7  <package-name>
{% endcodeblock%}
while using
{% codeblock Install 3.* Package install_package3.sh%}
easy_install-3.2  <package-name>
{% endcodeblock%}
to install version 3.* package.

(End)

