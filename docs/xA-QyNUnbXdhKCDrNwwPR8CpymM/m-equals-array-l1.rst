.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_Array_LREAL" %>
.. _`.fld-Assert.FB_Assert.M_Equals_Array_LREAL`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_Array_LREAL`:

FB_Assert.M_Equals_Array_LREAL (METH)
-------------------------------------

METHOD M_Equals_Array_LREAL : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_Array_LREAL

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+----------------------+------------------+----------------------------+
    | Scope  | Name                 | Type             | Comment                    |
    +========+======================+==================+============================+
    | Return | M_Equals_Array_LREAL | |ioI_Assert|     |                            |
    +--------+----------------------+------------------+----------------------------+
    | Input  | Expected             | POINTER TO LREAL | Expected as array of lreal |
    +        +----------------------+------------------+----------------------------+
    |        | Actual               | POINTER TO LREAL | Actual as array of lreal   |
    +        +----------------------+------------------+----------------------------+
    |        | Tolerance            | LREAL            | Tolerance as lreal         |
    +        +----------------------+------------------+----------------------------+
    |        | Message              | STRING(255)      | Message as string          |
    +--------+----------------------+------------------+----------------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



