.. first line of object.rst template
.. first line of dut-object.rst template
.. first line of struct-object.rst template
.. <% set key = ".fld-Testcase.ST_Testcase" %>
.. _`.fld-Testcase.ST_Testcase`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. Index::
   single: ST_Testcase

.. _`ST_Testcase`:

ST_Testcase (STRUCT)
--------------------

TYPE ST_Testcase : STRUCT


.. <% merge "object.Doc" %>

.. todo:: Please add documentation for struct: ST_Testcase

.. <% endmerge  %>

.. <% merge "object.iotbl" %>


InOut:
    +-------------+-------------+------------------------------------------------------------+
    | Name        | Type        | Comment                                                    |
    +=============+=============+============================================================+
    | sName       | STRING(255) | name        The name of this test case, often the method   |
    |             |             | name                                                       |
    +-------------+-------------+------------------------------------------------------------+
    | sClassname  | STRING(255) | classname   The name of the parent class/folder, often the |
    |             |             | same as the suite's name                                   |
    +-------------+-------------+------------------------------------------------------------+
    | nAssertions | DINT        | assertions  Number of assertions checked during test case  |
    |             |             | execution                                                  |
    +-------------+-------------+------------------------------------------------------------+
    | fTime       | LREAL       | time        Execution time of the test in seconds          |
    +-------------+-------------+------------------------------------------------------------+
    | sFile       | STRING(255) | file        Source code file of this test case             |
    +-------------+-------------+------------------------------------------------------------+
    | sLine       | STRING(255) | line        Source code line number of the start of this   |
    |             |             | test case                                                  |
    +-------------+-------------+------------------------------------------------------------+

.. <% endmerge  %>

.. last line of struct-object.rst template
.. last line of dut-object.rst template
.. last line of object.rst template



