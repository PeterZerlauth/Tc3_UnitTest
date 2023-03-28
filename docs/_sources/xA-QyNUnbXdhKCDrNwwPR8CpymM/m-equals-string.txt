.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals_STRING" %>
.. _`.fld-Assert.FB_Assert.M_Equals_STRING`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals_STRING`:

FB_Assert.M_Equals_STRING (METH)
--------------------------------

METHOD M_Equals_STRING : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals_STRING

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+-----------------+--------------+--------------------+
    | Scope  | Name            | Type         | Comment            |
    +========+=================+==============+====================+
    | Return | M_Equals_STRING | |ioI_Assert| |                    |
    +--------+-----------------+--------------+--------------------+
    | Input  | Expected        | STRING(255)  | Expected as string |
    +        +-----------------+--------------+--------------------+
    |        | Actual          | STRING(255)  | Actual as string   |
    +        +-----------------+--------------+--------------------+
    |        | Message         | STRING(255)  | Message as string  |
    +--------+-----------------+--------------+--------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



