.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.I_Assert.M_Equals_BOOL" %>
.. _`.fld-Assert.I_Assert.M_Equals_BOOL`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`I_Assert.M_Equals_BOOL`:

I_Assert.M_Equals_BOOL (METH)
-----------------------------

METHOD M_Equals_BOOL : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: I_Assert.M_Equals_BOOL

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+---------------+--------------+-------------------+
    | Scope  | Name          | Type         | Comment           |
    +========+===============+==============+===================+
    | Return | M_Equals_BOOL | |ioI_Assert| |                   |
    +--------+---------------+--------------+-------------------+
    | Input  | Expected      | BOOL         | Expected as bool  |
    +        +---------------+--------------+-------------------+
    |        | Actual        | BOOL         | Actual as bool    |
    +        +---------------+--------------+-------------------+
    |        | Message       | STRING(255)  | Message as string |
    +--------+---------------+--------------+-------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



