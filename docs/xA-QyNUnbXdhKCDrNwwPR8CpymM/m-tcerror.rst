.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_TcError" %>
.. _`.fld-Assert.FB_Assert.M_TcError`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_TcError`:

FB_Assert.M_TcError (METH)
--------------------------

METHOD M_TcError : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_TcError

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+-----------+--------------+-------------------+
    | Scope  | Name      | Type         | Comment           |
    +========+===========+==============+===================+
    | Return | M_TcError | |ioI_Assert| |                   |
    +--------+-----------+--------------+-------------------+
    | Input  | ErrorId   | UDINT        | ErrorId as UDINT  |
    +        +-----------+--------------+-------------------+
    |        | Message   | STRING(255)  | Message as string |
    +--------+-----------+--------------+-------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



