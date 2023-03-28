.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.I_Assert.M_Equals_UDINT" %>
.. _`.fld-Assert.I_Assert.M_Equals_UDINT`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`I_Assert.M_Equals_UDINT`:

I_Assert.M_Equals_UDINT (METH)
------------------------------

METHOD M_Equals_UDINT : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: I_Assert.M_Equals_UDINT

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+----------------+--------------+-------------------+
    | Scope  | Name           | Type         | Comment           |
    +========+================+==============+===================+
    | Return | M_Equals_UDINT | |ioI_Assert| |                   |
    +--------+----------------+--------------+-------------------+
    | Input  | Expected       | UDINT        | Expected as udint |
    +        +----------------+--------------+-------------------+
    |        | Actual         | UDINT        | Actual as udint   |
    +        +----------------+--------------+-------------------+
    |        | Message        | STRING(255)  | Message as string |
    +--------+----------------+--------------+-------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



