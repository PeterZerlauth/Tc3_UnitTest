.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_Array_REAL" %>
.. _`.fld-Assert.FB_Assert.M_Equals_Array_REAL`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_Array_REAL`:

FB_Assert.M_Equals_Array_REAL (METH)
------------------------------------

METHOD M_Equals_Array_REAL : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_Array_REAL

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+---------------------+-----------------+---------------------------+
    | Scope  | Name                | Type            | Comment                   |
    +========+=====================+=================+===========================+
    | Return | M_Equals_Array_REAL | |ioI_Assert|    |                           |
    +--------+---------------------+-----------------+---------------------------+
    | Input  | Expected            | POINTER TO REAL | Expected as array of real |
    +        +---------------------+-----------------+---------------------------+
    |        | Actual              | POINTER TO REAL | Actual as array of real   |
    +        +---------------------+-----------------+---------------------------+
    |        | Tolerance           | REAL            | Tolerance as real         |
    +        +---------------------+-----------------+---------------------------+
    |        | Message             | STRING(255)     | Message as string         |
    +--------+---------------------+-----------------+---------------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



