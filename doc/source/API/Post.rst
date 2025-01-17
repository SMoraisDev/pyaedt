Post-processing
===============
This section lists modules for creating and editing
plots in AEDT and shows how to interact with AEDT fields calculator.
They are accessible through the ``post`` property.

.. note::
   Some capabilities of the ``advanced_post_processing`` module require Python 3 and
   installations of the `numpy <https://numpy.org/doc/stable/>`_,
   `matplotlib <https://matplotlib.org/>`_, and `pyvista <https://docs.pyvista.org/>`_ 
   packages.

.. note::
   Some functionalities are available only when AEDT is running 
   in graphical mode.

Advanced post-processing
~~~~~~~~~~~~~~~~~~~~~~~~

.. currentmodule:: ansys.aedt.core.modules

.. autosummary::
   :toctree: _autosummary
   :nosignatures:

   advanced_post_processing.PostProcessor


.. code:: python

    from ansys.aedt.core import Hfss
    app = Hfss(specified_version="2023.1",
                 non_graphical=False, new_desktop_session=True,
                 close_on_exit=True, student_version=False)

    # This call returns the PostProcessor class
    post = app.post

    # This call returns a FieldPlot object
    plotf = post.create_fieldplot_volume(objects, quantity_name, setup_name, intrinsics)

    # This call returns a SolutionData object
    my_data = post.get_solution_data(expressions=trace_names)

    # This call returns a new standard report object and creates one or multiple reports from it.
    standard_report = post.reports_by_category.standard("db(S(1,1))")
    standard_report.create()
    sols = standard_report.get_solution_data()
    ...


AEDT report management
~~~~~~~~~~~~~~~~~~~~~~
AEDT provides great flexibility in reports.
PyAEDT has classes for manipulating any report property.


.. note::
   Some functionalities are available only when AEDT is running
   in graphical mode.


.. currentmodule:: ansys.aedt.core.modules

.. autosummary::
   :toctree: _autosummary
   :nosignatures:

   report_templates.Trace
   report_templates.LimitLine
   report_templates.Standard
   report_templates.Fields
   report_templates.NearField
   report_templates.FarField
   report_templates.EyeDiagram
   report_templates.Emission
   report_templates.Spectral

Icepak monitors
~~~~~~~~~~~~~~~
The ``monitor_icepak`` module includes the classes listed below to add, modify, and manage monitors during simulations.
Retrieve monitor values for post-processing and analysis to gain insights into key simulation metrics.
Methods and properties are accessible through the ``monitor`` property of the ``Icepak`` class.

.. currentmodule:: ansys.aedt.core.modules.monitor_icepak

.. autosummary::
   :toctree: _autosummary
   :nosignatures:


   FaceMonitor
   PointMonitor
   Monitor

Advanced fields calculator
~~~~~~~~~~~~~~~~~~~~~~~~~~
The ``fields_calculator`` module includes the ``FieldsCalculator`` class.
It provides methods to interact with AEDT Fields Calculator by adding, loading and deleting custom expressions.

.. currentmodule:: ansys.aedt.core.modules.fields_calculator

.. autosummary::
   :toctree: _autosummary
   :nosignatures:


   FieldsCalculator
