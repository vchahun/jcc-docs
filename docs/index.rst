.. JCC documentation master file, created by
   sphinx-quickstart on Fri Apr 27 18:47:28 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

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
2. Compile the jar into a module

::

	python -m jcc
		--jar boilerpipe-1.2.0.jar
		--classpath lib/nekohtml-1.9.13.jar
		--classpath lib/xerces-2.9.1.jar
		--package java.io
		java.io.BufferedReader
		java.io.FileReader
		--python boilerpipe --build --install

3. Use in yout python code!

::

    >>> import boilerpipe
    >>> jars = ['lib/nekohtml-1.9.13.jar', 'lib/xerces-2.9.1.jar']
    >>> boilerpipe.initVM(boilerpipe.CLASSPATH+':'+':'.join(jars))
    <jcc.JCCEnv object at 0x10f6f70f0>
    >>> extractor = boilerpipe.ArticleExtractor.getInstance()
    >>> file_reader = boilerpipe.FileReader('test.html')
    >>> buffered_reader = boilerpipe.BufferedReader(file_reader)
    >>> extractor.getText(buffered_reader)
    u'Your HTML converted to text!'


Colophon
========

The logo image is taken from `ClipArt ETC <http://etc.usf.edu/clipart/>`_.

This website is generated with `Sphinx <http://sphinx.pocoo.org>`_, using the
an adapted template from `Requests <http://docs.python-requests.org/>`_.

