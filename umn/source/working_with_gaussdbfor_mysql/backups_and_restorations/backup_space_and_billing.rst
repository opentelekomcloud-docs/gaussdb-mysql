:original_name: gaussdb_03_0069.html

.. _gaussdb_03_0069:

Backup Space and Billing
========================

Category
--------

-  The full backup mode is used to back up all target data even if no data is updated since the last backup.
-  Incremental backup: The system automatically backs up data that has changed since the last automated backup or incremental backup in binlogs every 5 minutes. The binlogs can be used to restore data to a specified point in time.
-  Differential backup: The system backs up data that has changed since the most recent full backup or differential backup in to physical files. Physical files cannot be used for log replay.
-  Billable space: Backup space that you are billed for.
-  Logical space: Space occupied by full backups.
-  Physical space: The amount of data that is backed up to OBS.

   .. note::

      After you create a DB instance, the logical space is the same as the physical space. When a backup starts in a backup chain, the physical space stores the data of the first full backup and subsequent differential backups.

Backup Space Calculation Methods
--------------------------------

There is a default backup chain (where there are seven backups). The first automated backup is a full backup, and subsequent automated backups are differential backups.

In a backup chain, the backup space is released only after all full backups and differential backups are deleted.

-  Logical space: Total size of the logical space - Logical size of the expired backup file
-  Physical space: Size of the first full backup file + total size of subsequent differential backup files
-  Free space: There is free backup storage up to 100% of your provisioned database storage.

Billing is calculated as follows:

The system deducts the free space from either the logical space or the physical space, whichever is smaller.

Example
-------

A backup line contains seven backups by default. There are 11 backups shown in the following figure. The 1st backup to the 7th belong to one backup line and the 8th to the 11th belong to another.


.. figure:: /_static/images/en-us_image_0000001896928157.png
   :alt: **Figure 1** Backup example

   **Figure 1** Backup example

If there is 1,000 MB of backup space and the logical space is 1,000 MB each time, the physical space for the 1st backup is 1,000 MB. If the incremental data size is 100 MB each time, the physical space for the 2nd backup to 7th is 100 MB.

A backup line contains seven backups by default. The physical space for the 8th backup is 1,000 MB because it represents a new backup line.

Billed space includes the space of the two chains in the example.

Suppose that after the 11th backup was created, and the 1st, 2nd and 3rd backups expired and were automatically deleted. The size of each space is calculated as follows:

-  Total logical space size = Total logical space size - Logical size of the expired backup file (1,000 MB x 11 - 3,000 MB = 8,000 MB in this example).
-  Physical space: size of data backed up to OBS. In this example, physical space includes the sum of physical space on the two backup links: 1,000 MB + (100 MB x 6) +1,000 MB+ (100 MB X 3) =2,900 MB
-  Total billed space = Min (Total size of logical space, Total size of physical space) - free space, so the total billed space in this example = Min (8,000 MB, 2,900 MB) - 1,000 MB = 1,900 MB
