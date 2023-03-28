.. first line of object.rst template
.. first line of pou-object.rst template
.. first line of meth-object.rst template
.. <% set key = ".fld-Testsuite.FB_Testsuite.M_Testcase" %>
.. _`.fld-Testsuite.FB_Testsuite.M_Testcase`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. _`FB_Testsuite.M_Testcase`:

FB_Testsuite.M_Testcase (METH)
------------------------------

METHOD M_Testcase : BOOL



.. <% merge "object.Doc" %>

.. todo:: Please add documentation for method: FB_Testsuite.M_Testcase

.. <% endmerge  %>

.. <% merge "object.iotbl" %>



InOut:
    +--------+------------+-------------+----------------------+
    | Scope  | Name       | Type        | Comment              |
    +========+============+=============+======================+
    | Return | M_Testcase | BOOL        |                      |
    +--------+------------+-------------+----------------------+
    | Input  | Classname  | STRING(255) | Classname as string  |
    +        +------------+-------------+----------------------+
    |        | Timeout    | TIME        | Timeout as time      |
    +        +------------+-------------+----------------------+
    |        | File       | STRING(255) | File as string       |
    +        +------------+-------------+----------------------+
    |        | Line       | STRING(255) | Line as string       |
    +        +------------+-------------+----------------------+
    |        | Next       | INT         | Next Testcase as int |
    +--------+------------+-------------+----------------------+

.. <% endmerge  %>

.. last line of meth-object.rst template
.. last line of pou-object.rst template
.. last line of object.rst template



