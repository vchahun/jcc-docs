===
JCC
===

JCC_ is a C++ code generator for calling Java from C++ and Python.

Installation
============

If you use Ubuntu, you can install the ``jcc`` package included in the official 
repositories::

    sudo apt-get install jcc

JCC is also available from PyPI, so you can install it using ``pip``::

    pip install jcc

Please refer to the `original documentation`__ to see how to install it on 
other platforms or to build it from the source.

__ http://lucene.apache.org/pylucene/jcc/install.html

Example
=======

This example shows how to use boilerpipe_, a library for extracting text from 
HTML pages, directly in Python.

#. Download the most recent `binary tarball`__ (for example, `version 
   1.2.0`__).

#. Extract the downloaded file::
    
    tar xvzf boilerpipe-*.tar.gz
    cd boilerpipe-*

#. Compile the jar file into a Python module::

    python -m jcc \
        --jar boilerpipe-1.2.0.jar \
        --classpath lib/nekohtml-1.9.13.jar \
        --classpath lib/xerces-2.9.1.jar \
        --package java.net \
        java.net.URL \
        --python boilerpipe --build --install

#. Now you can use in your Python code!::

    >>> import boilerpipe
    >>> jars = ':'.join(('lib/nekohtml-1.9.13.jar', 'lib/xerces-2.9.1.jar'))
    >>> boilerpipe.initVM(boilerpipe.CLASSPATH+':'+jars)
    <jcc.JCCEnv object at 0x10f6f70f0>
    >>> extractor = boilerpipe.ArticleExtractor.getInstance()
    >>> url = boilerpipe.URL('http://readthedocs.org/docs/jcc')
    >>> extractor.getText(url)[:24]
    u'Download boilerpipe from'


.. _boilerpipe: http://code.google.com/p/boilerpipe/
__ http://code.google.com/p/boilerpipe/downloads/list
__ http://boilerpipe.googlecode.com/files/boilerpipe-1.2.0-bin.tar.gz



Colophon
========

This is the *unofficial* documentation of JCC. It is an ongoing project to make 
it easier to use and to include more examples. Please refer to the JCC_ website 
and for the complete documentation__. 

.. _JCC: http://lucene.apache.org/pylucene/jcc/
__ http://lucene.apache.org/pylucene/jcc/readme.html

The logo image is taken from `ClipArt ETC <http://etc.usf.edu/clipart/>`_.

This website is generated with `Sphinx <http://sphinx.pocoo.org>`_, using the
an adapted template from `Requests <http://docs.python-requests.org/>`_.
