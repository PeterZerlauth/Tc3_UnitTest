.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_ULINT" %>
.. _`.fld-Assert.FB_Assert.M_Equals_ULINT`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_ULINT`:

FB_Assert.M_Equals_ULINT (METH)
-------------------------------

METHOD M_Equals_ULINT : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_ULINT

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+----------------+--------------+-------------------+
    | Scope  | Name           | Type         | Comment           |
    +========+================+==============+===================+
    | Return | M_Equals_ULINT | |ioI_Assert| |                   |
    +--------+----------------+--------------+-------------------+
    | Input  | Expected       | ULINT        | Expected as ulint |
    +        +----------------+--------------+-------------------+
    |        | Actual         | ULINT        | Actual as ulint   |
    +        +----------------+--------------+-------------------+
    |        | Message        | STRING(255)  | Message as string |
    +--------+----------------+--------------+-------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



