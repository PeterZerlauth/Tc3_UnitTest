.. first line of object.rst template
.. first line of dut-object.rst template
.. first line of struct-object.rst template
.. <% set key = ".fld-Logger.ST_Logger" %>
.. _`.fld-Logger.ST_Logger`:
.. <% merge "object.Defines" %>
.. <% endmerge  %>


.. Index::
   single: ST_Logger

.. _`ST_Logger`:

ST_Logger (STRUCT)
------------------

TYPE ST_Logger : STRUCT


.. <% merge "object.Doc" %>

.. todo:: Please add documentation for struct: ST_Logger

.. <% endmerge  %>

.. <% merge "object.iotbl" %>


InOut:
    +------------------+----------------+---------------------+
    | Name             | Type           | Initial             |
    +==================+================+=====================+
    | eLogLevelMinimum | |ioE_LogLevel| | E_LogLevel.Debug    |
    +------------------+----------------+---------------------+
    | eLogLevelMaximum | |ioE_LogLevel| | E_LogLevel.Critical |
    +------------------+----------------+---------------------+

.. |ioE_LogLevel| replace:: :ref:`E_LogLevel<E_LogLevel>`


.. <% endmerge  %>

.. last line of struct-object.rst template
.. last line of dut-object.rst template
.. last line of object.rst template



