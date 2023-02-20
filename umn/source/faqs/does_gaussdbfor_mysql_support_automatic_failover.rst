:original_name: gaussdb_faq_0005.html

.. _gaussdb_faq_0005:

Does GaussDB(for MySQL) Support Automatic Failover?
===================================================

During the creation of a GaussDB(for MySQL) DB instance, a read replica is created by default in addition to a primary node. If the primary node fails, the system automatically fails over to a read replica with the highest priority and the original primary node is restored in the background.
