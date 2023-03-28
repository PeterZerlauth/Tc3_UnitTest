.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_Array_LINT" %>
.. _`.fld-Assert.FB_Assert.M_Equals_Array_LINT`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_Array_LINT`:

FB_Assert.M_Equals_Array_LINT (METH)
------------------------------------

METHOD M_Equals_Array_LINT : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_Array_LINT

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+---------------------+-----------------+---------------------------+
    | Scope  | Name                | Type            | Comment                   |
    +========+=====================+=================+===========================+
    | Return | M_Equals_Array_LINT | |ioI_Assert|    |                           |
    +--------+---------------------+-----------------+---------------------------+
    | Input  | Expected            | POINTER TO LINT | Expected as array of lint |
    +        +---------------------+-----------------+---------------------------+
    |        | Actual              | POINTER TO LINT | Actual as array of lint   |
    +        +---------------------+-----------------+---------------------------+
    |        | Message             | STRING(255)     | Message as string         |
    +--------+---------------------+-----------------+---------------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



