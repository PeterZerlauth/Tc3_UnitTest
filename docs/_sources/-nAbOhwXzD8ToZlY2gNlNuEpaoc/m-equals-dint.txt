.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.I_Assert.M_Equals_DINT" %>
.. _`.fld-Assert.I_Assert.M_Equals_DINT`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`I_Assert.M_Equals_DINT`:

I_Assert.M_Equals_DINT (METH)
-----------------------------

METHOD M_Equals_DINT : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: I_Assert.M_Equals_DINT

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+---------------+--------------+-------------------+
    | Scope  | Name          | Type         | Comment           |
    +========+===============+==============+===================+
    | Return | M_Equals_DINT | |ioI_Assert| |                   |
    +--------+---------------+--------------+-------------------+
    | Input  | Expected      | DINT         | Expected as dint  |
    +        +---------------+--------------+-------------------+
    |        | Actual        | DINT         | Actual as dint    |
    +        +---------------+--------------+-------------------+
    |        | Message       | STRING(255)  | Message as string |
    +--------+---------------+--------------+-------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



