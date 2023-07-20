:original_name: gaussdb_03_0087.html

.. _gaussdb_03_0087:

Setting Alarm Rules
===================

Scenarios
---------

You can set alarm rules for GaussDB(for MySQL) to customize the monitored objects and notification policies and stay aware of the GaussDB(for MySQL) operating status.

The GaussDB(for MySQL) alarm rules include alarm rule names, services, dimensions, monitored objects, metrics, alarm thresholds, monitoring period, and whether to send notifications.

Procedure
---------

#. Log in to the management console.

#. Under **Management & Deployment**, click **Cloud Eye**.

#. In the navigation pane on the left, choose **Cloud Service Monitoring** > **GaussDB(for MySQL)**.

#. Locate the DB instance for which you want to create an alarm rule and click |image1| on the left, and then click **Create Alarm Rule** in the **Operation** column.

#. On the displayed page, set parameters as required.

   -  Specify **Name** and **Description**.
   -  Select **Use template** for **Method**. The template contains the following common metrics: CPU usage, memory usage, and storage space usage.
   -  Click |image2| to enable alarm notification. The validity period is 24 hours by default. If the topics you require are not displayed in the drop-down list, click **Create an SMN topic**. Then, select **Generated alarm** and **Cleared alarm** for **Trigger Condition**.

      .. note::

         Cloud Eye sends notifications only within the validity period specified in the alarm rule.

#. Click **Create**. The alarm rule is created.

   For operation details, see the *Cloud Eye User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001403218685.png
.. |image2| image:: /_static/images/en-us_image_0000001352538844.png
