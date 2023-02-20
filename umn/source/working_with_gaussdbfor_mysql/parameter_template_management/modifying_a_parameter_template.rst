:original_name: gaussdb_08_0112.html

.. _gaussdb_08_0112:

Modifying a Parameter Template
==============================

You can modify parameters in a custom parameter template to optimize GaussDB(for MySQL) database performance.

You can change parameter values in custom parameter templates only, but cannot change parameter values in default parameter templates. When you change parameter values in a custom parameter template, the changes take effect for all DB instances to which the parameter template applies.

.. note::

   GaussDB(for MySQL) has default parameter templates whose parameter values cannot be changed. You can view these parameter values by clicking the default parameter templates. If a custom parameter template is set incorrectly and causes a database reboot to fail, you can re-configure the custom parameter template according to the configurations of the default parameter template.

Modifying Parameter Template Parameters
---------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **GaussDB**.

#. In the navigation pane on the left, choose **Parameter Template Management**. On the **Custom Templates** page, click the parameter template you want to view.

#. Modify parameters as required.

   Available operations are as follows:

   .. important::

      After you modify parameters in a parameter template, some modifications immediately take effect for the DB instance to which the parameter template applies. Exercise caution when performing this operation.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After the parameters are modified, you can click **Change History** to view the modification details.

   .. important::

      The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <gaussdb_05_0018>`.

   -  After modifying some parameters of a DB instance, you need to reboot the DB instance for the modifications to take effect.
   -  After modifying some parameters of a read replica, you need to reboot the read replica for the modifications to take effect.

Modifying Instance Parameters
-----------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **GaussDB**.

#. On the **Instance Management** page, click the target DB instance. The **Basic Information** page is displayed.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   Available operations are as follows:

   .. important::

      After you modify instance parameters, the modifications immediately take effect for the DB instance.

      Check the value in the **Effective upon Reboot** column.

      -  If the value is **Yes** and the DB instance status on the **Instance Management** page is **Pending reboot**, you must reboot the DB instance for the modifications to take effect.
      -  If the value is **No**, the modifications take effect immediately.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

   After parameters are modified, you can click **Change History** to view parameter modification details.

.. |image1| image:: /_static/images/en-us_image_0000001400783488.png
.. |image2| image:: /_static/images/en-us_image_0000001400783488.png
