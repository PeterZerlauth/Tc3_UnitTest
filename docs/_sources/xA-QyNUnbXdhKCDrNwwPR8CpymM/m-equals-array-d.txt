.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_Array_DINT" %>
.. _`.fld-Assert.FB_Assert.M_Equals_Array_DINT`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_Array_DINT`:

FB_Assert.M_Equals_Array_DINT (METH)
------------------------------------

METHOD M_Equals_Array_DINT : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_Array_DINT

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+---------------------+-----------------+---------------------------+
    | Scope  | Name                | Type            | Comment                   |
    +========+=====================+=================+===========================+
    | Return | M_Equals_Array_DINT | |ioI_Assert|    |                           |
    +--------+---------------------+-----------------+---------------------------+
    | Input  | Expected            | POINTER TO DINT | Expected as array of dint |
    +        +---------------------+-----------------+---------------------------+
    |        | Actual              | POINTER TO DINT | Actual as array of dint   |
    +        +---------------------+-----------------+---------------------------+
    |        | Message             | STRING(255)     | Message as string         |
    +--------+---------------------+-----------------+---------------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



