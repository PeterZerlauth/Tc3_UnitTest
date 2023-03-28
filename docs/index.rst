.. first line of index.rst template
.. <% set key = "." %>
.. <% merge "index.Shortcuts" %>
.. <% endmerge %>

.. <% merge "index.Title" -%>
.. _index:

=================================
Tc3_Testing Library Documentation
=================================

.. <%- endmerge %>

.. <% merge "index.ProjectInfo" -%>

:Company: Zerlauth
:Title: Tc3_Testing
:Version: 0.0.0.21
:Categories: Automaiton
:Namespace: Tc3_Testing
:Author: Peter Zerlauth
:Placeholder: Tc3_Testing

.. <%- endmerge %>

.. _index_description:

Description [1]_
----------------

.. <% merge "index.Description" -%>

Twincat 3 unit test library

.. <%- endmerge %>

Contents:
---------

.. toctree::
   :maxdepth: 2

   /QUGt1FomRZxL05kJOISCMR9v4po/fld-Assert
   /B3_pxU7V7Sb6VH9N7T75qbsGbWU/fld-Base
   /LDyvpNs_Ph5Rs9_0MDUC2-Qreok/fld-File
   /of_6qvt8yZZoW864KcBTzE995D0/fld-List
   /hDLCRXPz-J-tYIAv6O3fHaYxV2g/fld-Logger
   /UAiDZv4Sl3Rupe4DyH3ut_6uycc/fld-Testcase
   /Kbramgl5nYvf8Q7yPNCJ6VSfqeE/fld-Testsuite
   /owlYETu2T4Wo3CGBvSY2ZkJeEYY/fld-Testsuites

Indices and tables
------------------

.. toctree::
   :hidden:

   info
   libraries

.. only:: libdoc_html

    * :ref:`genindex`
    * :ref:`search`
    * :ref:`info`
    * :ref:`libraries`

.. only:: libdoc_chm

    * :ref:`info`
    * :ref:`libraries`

.. only:: libdoc_lmd

    * :ref:`info`
    * :ref:`libraries`

.. <% merge "index.SourceRelation" %>
.. [1] | Based on tc3_testing.library, last modified 24.03.2023, 22:08:57.
       | The content file Tc3_Testing.clean.json was generated with TwinCAT PLC Control_Build_4024.42 on 28.03.2023, 21:12:54
.. <% endmerge %>
.. last line of index.rst template
