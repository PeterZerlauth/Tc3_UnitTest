.. first line of object.rst template
.. first line of dut-object.rst template
.. first line of struct-object.rst template
.. <% set key = ".fld-Testsuites.ST_Testsuites" %>
.. _`.fld-Testsuites.ST_Testsuites`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. Index::
   single: ST_Testsuites

.. _`ST_Testsuites`:

ST_Testsuites (STRUCT)
----------------------

TYPE ST_Testsuites : STRUCT


.. <% merge "object.Doc" %>

.. todo:: Please add documentation for struct: ST_Testsuites

.. <% endmerge  %>

.. <% merge "object.iotbl" %>


InOut:
    +-------------+-------------+-------------------------------------------------------+
    | Name        | Type        | Comment                                               |
    +=============+=============+=======================================================+
    | sName       | STRING(255) | Name OF the entire test run                           |
    +-------------+-------------+-------------------------------------------------------+
    | nTests      | DINT        | Total number of tests in this file                    |
    +-------------+-------------+-------------------------------------------------------+
    | nFailures   | DINT        | Total number of failed tests in this file             |
    +-------------+-------------+-------------------------------------------------------+
    | nErrors     | DINT        | Total number of errored tests in this file            |
    +-------------+-------------+-------------------------------------------------------+
    | nSkipped    | DINT        | Total number of skipped tests in this file            |
    +-------------+-------------+-------------------------------------------------------+
    | nAssertions | DINT        | Total number of assertions for all tests in this file |
    +-------------+-------------+-------------------------------------------------------+
    | fTime       | LREAL       | Aggregated time of all tests in this file in seconds  |
    +-------------+-------------+-------------------------------------------------------+
    | sTimestamp  | STRING(39)  | timestamp   Date and time of when the test suite was  |
    |             |             | executed (in ISO 8601 format)                         |
    +-------------+-------------+-------------------------------------------------------+

.. <% endmerge  %>

.. last line of struct-object.rst template
.. last line of dut-object.rst template
.. last line of object.rst template



