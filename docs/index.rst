===
JCC
===

A C++ code generator for calling Java from C++/Python.

Installation
============

::

    pip install jcc

Example
=======

1. Download boilerpipe from http://code.google.com/p/boilerpipe

::
    
    tar xvzf boilerpipe-*.tar.gz
    cd boilerpipe-*

2. Compile the jar into a module

::

    python -m jcc \
        --jar boilerpipe-1.2.0.jar \
        --classpath lib/nekohtml-1.9.13.jar \
        --classpath lib/xerces-2.9.1.jar \
        --package java.net \
        java.net.URL \
        --python boilerpipe --build --install

3. Use in yout python code!

::

    >>> import boilerpipe
    >>> jars = ':'.join(('lib/nekohtml-1.9.13.jar', 'lib/xerces-2.9.1.jar'))
    >>> boilerpipe.initVM(boilerpipe.CLASSPATH+':'+jars)
    <jcc.JCCEnv object at 0x10f6f70f0>
    >>> extractor = boilerpipe.ArticleExtractor.getInstance()
    >>> url = boilerpipe.URL("http://pypi.python.org/pypi/JCC")
    >>> extractor.getText(url)[:24]
    u'Download boilerpipe from'


Colophon
========

The logo image is taken from `ClipArt ETC <http://etc.usf.edu/clipart/>`_.

This website is generated with `Sphinx <http://sphinx.pocoo.org>`_, using the
an adapted template from `Requests <http://docs.python-requests.org/>`_.
