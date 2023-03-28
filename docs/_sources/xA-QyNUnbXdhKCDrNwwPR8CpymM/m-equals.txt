.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Assert.FB_Assert.M_Equals" %>
.. _`.fld-Assert.FB_Assert.M_Equals`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Assert.M_Equals`:

FB_Assert.M_Equals (METH)
-------------------------

METHOD M_Equals : |dI_Assert|

.. |dI_Assert| replace:: :ref:`I_Assert<I_Assert>`

.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Assert.M_Equals

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+----------+-------------------+-------------------+
    | Scope  | Name     | Type              | Comment           |
    +========+==========+===================+===================+
    | Return | M_Equals | |ioI_Assert|      |                   |
    +--------+----------+-------------------+-------------------+
    | Input  | Expected | \__SYSTEM.AnyType | Expected          |
    +        +----------+-------------------+-------------------+
    |        | Actual   | \__SYSTEM.AnyType | Actual            |
    +        +----------+-------------------+-------------------+
    |        | Message  | STRING(255)       | Message as string |
    +--------+----------+-------------------+-------------------+

.. |ioI_Assert| replace:: :ref:`I_Assert<I_Assert>`


.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



