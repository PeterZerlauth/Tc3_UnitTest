.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.I_Assert.M_Equals_LINT" %>
.. _`.fld-Assert.I_Assert.M_Equals_LINT`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`I_Assert.M_Equals_LINT`:

I_Assert.M_Equals_LINT (METH)
-----------------------------

METHOD M_Equals_LINT : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: I_Assert.M_Equals_LINT

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+---------------+--------------+-------------------+
    | Scope  | Name          | Type         | Comment           |
    +========+===============+==============+===================+
    | Return | M_Equals_LINT | |ioI_Assert| |                   |
    +--------+---------------+--------------+-------------------+
    | Input  | Expected      | LINT         | Expected as lint  |
    +        +---------------+--------------+-------------------+
    |        | Actual        | LINT         | Actual as lint    |
    +        +---------------+--------------+-------------------+
    |        | Message       | STRING(255)  | Message as string |
    +--------+---------------+--------------+-------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



