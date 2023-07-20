:original_name: gaussdb_11_0021.html

.. _gaussdb_11_0021:

Testing Read/Write Splitting Performance
========================================

After read/write splitting is enabled, databases can be connected through a read/write splitting address. You can use internal SQL commands to verify the read/write splitting performance.

Procedure
---------

#. Use a read/write splitting address to connect to the database. For details, see :ref:`Enabling Read/Write Splitting <gaussdb_11_0017>`.

#. Run the following command to view the routing result of the previous SQL statement. The result is the private IP address of the DB instance.

   .. code-block:: text

      show last route;


   .. figure:: /_static/images/en-us_image_0000001420606766.png
      :alt: **Figure 1** Query result

      **Figure 1** Query result
