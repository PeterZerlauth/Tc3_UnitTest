.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_Array_INT" %>
.. _`.fld-Assert.FB_Assert.M_Equals_Array_INT`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_Array_INT`:

FB_Assert.M_Equals_Array_INT (METH)
-----------------------------------

METHOD M_Equals_Array_INT : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_Array_INT

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+--------------------+----------------+--------------------------+
    | Scope  | Name               | Type           | Comment                  |
    +========+====================+================+==========================+
    | Return | M_Equals_Array_INT | |ioI_Assert|   |                          |
    +--------+--------------------+----------------+--------------------------+
    | Input  | Expected           | POINTER TO INT | Expected as array of int |
    +        +--------------------+----------------+--------------------------+
    |        | Actual             | POINTER TO INT | Actual as array of int   |
    +        +--------------------+----------------+--------------------------+
    |        | Message            | STRING(255)    | Message as string        |
    +--------+--------------------+----------------+--------------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



