:original_name: gaussdb_08_0015.html

.. _gaussdb_08_0015:

Resetting a Parameter Template
==============================

Scenarios
---------

You can reset all parameters in a custom parameter template to their default settings.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Database**, click **GaussDB**.
#. On the **Parameter Template Management** page, click **Custom Templates**. Locate the target parameter template and choose **More** > **Reset** in the **Operation** column.
#. Click **Yes**.

   .. note::

      After you reset a parameter template, click the DB instance to which the parameter template is applied to view the status of the parameter template. On the displayed **Basic Information** page, if the status of the parameter template is **Pending reboot**, you must reboot the DB instance for the reset to take effect.

.. |image1| image:: /_static/images/en-us_image_0000001400783488.png
