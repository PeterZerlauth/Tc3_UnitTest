.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_Array_BYTE" %>
.. _`.fld-Assert.FB_Assert.M_Equals_Array_BYTE`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_Array_BYTE`:

FB_Assert.M_Equals_Array_BYTE (METH)
------------------------------------

METHOD M_Equals_Array_BYTE : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_Array_BYTE

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+---------------------+-----------------+---------------------------+
    | Scope  | Name                | Type            | Comment                   |
    +========+=====================+=================+===========================+
    | Return | M_Equals_Array_BYTE | |ioI_Assert|    |                           |
    +--------+---------------------+-----------------+---------------------------+
    | Input  | Expected            | POINTER TO BYTE | Expected as array of byte |
    +        +---------------------+-----------------+---------------------------+
    |        | Actual              | POINTER TO BYTE | Actual as array of byte   |
    +        +---------------------+-----------------+---------------------------+
    |        | Message             | STRING(255)     | Message as string         |
    +--------+---------------------+-----------------+---------------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



