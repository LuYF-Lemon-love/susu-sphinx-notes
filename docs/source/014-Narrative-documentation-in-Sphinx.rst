014 Narrative documentation in Sphinx
=====================================

源教程地址: https://www.sphinx-doc.org/en/master/tutorial/narrative-documentation.html .

Structuring your documentation across multiple pages
----------------------------------------------------

The file index.rst created by sphinx-quickstart is the root document, 
whose main function is to serve as a welcome page 
and to contain the root of the “table of contents tree” (or toctree). 
Sphinx allows you to assemble a project from different files, 
which is helpful when the project grows.

As an example, create a new file ``docs/source/usage.rst`` (next to index.rst) with these contents:

**docs/source/usage.rst**

::

 Usage
 =====
 
 Installation
 ------------
 
 To use Lumache, first install it using pip:
 
 .. code-block:: console
 
    (.venv) $ pip install lumache

.. code-block:: console

   (.venv) $ pip install lumache

This new file contains two section headers, 
normal paragraph text, and a ``code-block directive`` 
that renders a block of content as source code, 
with appropriate syntax highlighting (in this case, generic console text).

The structure of the document is determined by the succession of heading styles, 
which means that, by using ``---`` for the “Installation” section 
after ``===`` for the “Usage” section, 
you have declared “Installation” to be a subsection of “Usage”.

To complete the process, add a ``toctree directive`` at the end of ``index.rst`` 
including the document you just created, as follows:

**docs/source/index.rst**

::

 Contents
 --------
 
 .. toctree::
 
    usage

This step inserts that document in the root of the toctree, 
so now it belongs to the structure of your project, which so far looks like this:

::

 index
 └── usage

If you build the HTML documentation running make html, 
you will see that the toctree gets rendered as a list of hyperlinks, 
and this allows you to navigate to the new page you just created. Neat!

.. warning::

   Documents outside a toctree will result in WARNING: 
   document isn't included in any toctree messages during the build process, 
   and will be unreachable for users.

Adding cross-references
-----------------------

One powerful feature of Sphinx is the ability to seamlessly 
add cross-references to specific parts of the documentation: a document, a section, 
a figure, a code object, etc. This tutorial is full of them!

To add a **cross-reference**, write this sentence right after the introduction paragraph 
in ``index.rst``:

**docs/source/index.rst**

::

 Check out the :doc:`usage` section for further information.

Check out the :doc:`usage` section for further information.

The doc role you used automatically references a specific document in the project, 
in this case the ``usage.rst`` you created earlier.

Alternatively, you can also add a cross-reference to an arbitrary part of the project. 
For that, you need to use the ref role, and add an explicit ``label`` that acts as a target.

For example, to reference the “Installation” subsection, 
add a label right before the heading, as follows:

**docs/source/usage.rst**

::

 Usage
 =====
 
 .. _installation:
 
 Installation
 ------------
 
 ...

And make the sentence you added in ``index.rst`` look like this:

**docs/source/index.rst**

::

 Check out the :doc:`usage` section for further information, including how to
 :ref:`install <installation>` the project.

Check out the :doc:`usage` section for further information, including how to
:ref:`install <installation>` the project.

Notice a trick here: the install part specifies how the link will 
look like (we want it to be a specific word, so the sentence makes sense), 
whereas the <installation> part refers to the actual label we want to 
add a cross-reference to. If you do not include an explicit title, 
hence using ``:ref:`installation``` (:ref:`installation`), the section title will be used (in this case, Installation). 
Both the ``:doc:`` and the ``:ref:`` roles will be rendered as hyperlinks in the HTML documentation.

What about documenting code objects in Sphinx? Read on!