002 Getting started with Sphinx
===============================

源教程地址: https://docs.readthedocs.io/en/stable/intro/getting-started-with-sphinx.html .

.. meta::
   :description lang=en: Get started writing technical documentation with Sphinx and publishing to Read the Docs.

Sphinx is a powerful documentation generator that
has many great features for writing technical documentation including:

* Generate web pages, printable PDFs, documents for e-readers (ePub),
  and more all from the same sources
* You can use reStructuredText or **Markdown**
  to write documentation
* An extensive system of cross-referencing code and documentation
* Syntax highlighted code samples
* A vibrant ecosystem of first and third-party :doc:`extensions <sphinx:usage/extensions/index>`

If you want to learn more about how to create your first Sphinx project, read on.
If you are interested in exploring the Read the Docs platform using an already existing Sphinx project,
check out `Read the Docs tutorial <https://docs.readthedocs.io/en/stable/tutorial/index.html>`_ .

Quick start
-----------

.. seealso:: If you already have a Sphinx project, check out our `Importing your documentation <https://docs.readthedocs.io/en/stable/intro/import-guide.html>`_ guide.

Assuming you have Python already, :doc:`install Sphinx <sphinx:usage/installation>`:

.. prompt:: bash $

    pip install sphinx

Create a directory inside your project to hold your docs:

.. prompt:: bash $

    cd /path/to/project
    mkdir docs

Run ``sphinx-quickstart`` in there:

.. prompt:: bash $

    cd docs
    sphinx-quickstart

This quick start will walk you through creating the basic configuration; in most cases, you
can just accept the defaults. When it's done, you'll have an ``index.rst``, a
``conf.py`` and some other files. Add these to revision control.

Now, edit your ``index.rst`` and add some information about your project.
Include as much detail as you like (refer to the :doc:`reStructuredText syntax <sphinx:usage/restructuredtext/basics>`
or `this template`_ if you need help). Build them to see how they look:

.. prompt:: bash $

    make html

Your ``index.rst`` has been built into ``index.html``
in your documentation output directory (typically ``_build/html/index.html``).
Open this file in your web browser to see your docs.

.. figure:: ../images/002-sphinx-hello-world.webp
   :figwidth: 500px
   :align: center

   Your Sphinx project is built

Edit your files and rebuild until you like what you see, then commit your changes and push to your public repository.
Once you have Sphinx documentation in a public repository, you can start using Read the Docs
by `importing your docs <https://docs.readthedocs.io/en/stable/intro/import-guide.html>`_.

.. warning::

   We strongly recommend to `pin the Sphinx version <https://docs.readthedocs.io/en/stable/guides/reproducible-builds.html>`_
   used for your project to build the docs to avoid potential future incompatibilities.

.. _this template: https://www.writethedocs.org/guide/writing/beginners-guide-to-docs/#id1

Using Markdown with Sphinx
--------------------------

You can use `Markdown using MyST`_ and reStructuredText in the same Sphinx project.
We support this natively on Read the Docs, and you can do it locally:

.. prompt:: bash $

    pip install myst-parser

Then in your ``conf.py``:

.. code-block:: python

   extensions = ["myst_parser"]

You can now continue writing your docs in ``.md`` files and it will work with Sphinx.
Read the `Getting started with MyST in Sphinx`_ docs for additional instructions.

.. _Getting started with MyST in Sphinx: https://myst-parser.readthedocs.io/en/latest/sphinx/intro.html
.. _Markdown using MyST: https://myst-parser.readthedocs.io/en/latest/using/intro.html


Get inspired!
-------------

You might learn more and find the first ingredients for starting your own documentation project by looking at `Example projects <https://docs.readthedocs.io/en/stable/examples.html>`_ - view live example renditions and copy & paste from the accompanying source code.


External resources
------------------

Here are some external resources to help you learn more about Sphinx.

* `Sphinx documentation`_
* :doc:`RestructuredText primer <sphinx:usage/restructuredtext/basics>`
* `An introduction to Sphinx and Read the Docs for technical writers`_

.. _Sphinx documentation: https://www.sphinx-doc.org/
.. _An introduction to Sphinx and Read the Docs for technical writers: https://www.ericholscher.com/blog/2016/jul/1/sphinx-and-rtd-for-writers/