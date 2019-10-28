Metrics
=======

Request
-------

``zenko-mgob:8090/metrics``


Response
--------

A successful backups counter request returns a message resembling::

   mgob_scheduler_backup_total{plan="metadata",status="200"} 8

A successful backups duration request returns a message resembling:

.. code:: 

   mgob_scheduler_backup_latency{plan="metadata",status="200",quantile="0.5"} 2.149668417
   mgob_scheduler_backup_latency{plan="metadata",status="200",quantile="0.9"} 2.39848413
   mgob_scheduler_backup_latency{plan="metadata",status="200",quantile="0.99"} 2.39848413
   mgob_scheduler_backup_latency_sum{plan="metadata",status="200"} 17.580484907
   mgob_scheduler_backup_latency_count{plan="metadata",status="200"} 8

A failed (status 500) jobs count and duration request resembles:

.. code:: bash

   mgob_scheduler_backup_latency{plan="mongo-test",status="500",quantile="0.5"} 2.4180213
   mgob_scheduler_backup_latency{plan="mongo-test",status="500",quantile="0.9"} 2.438254775
   mgob_scheduler_backup_latency{plan="mongo-test",status="500",quantile="0.99"} 2.438254775
   mgob_scheduler_backup_latency_sum{plan="mongo-test",status="500"} 9.679809477
   mgob_scheduler_backup_latency_count{plan="mongo-test",status="500"} 4
