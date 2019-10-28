Scheduler Status
================

Request
-------

- GET ``zenko-mgob:8090/status``
- GET ``zenko-mgob:8090/status/:planID``

Sample
~~~~~~

.. code:: bash

   curl -X GET http://zenko-mgob:8090/status/metadata

Response
--------

.. code:: json

      {
        "plan": "metadata",
        "next_run": "2019-09-06T05:00:00Z"
        "last_run": "2017-09-05T21:49:00.000622589Z",
        "last_run_status": "200",
        "last_run_log": "Backup finished in 2.339055539s archive metadata-1567720190.gz size 4.7 kB"
      }

Logs
~~~~

View scheduler logs with ``kubectl logs {{release-name}}-mgob-0``. This returns
information resembling:

.. code:: bash

   time="2019-09-05T21:49:38Z" level=info msg="Next tmp cleanup run at 2019-09-05 22:00:00 +0000 UTC"
   time="2019-09-05T21:49:38Z" level=info msg="Next run at 2019-09-06 05:00:00 +0000 UTC" plan=metadata
   time="2019-09-05T21:49:38Z" level=info msg="starting http server on port 8090"
   time="2019-09-05T21:49:50Z" level=info msg="On demand backup started" plan=metadata
   time="2019-09-05T21:49:50Z" level=info msg="new dump" archive="/tmp/metadata-1567720190.gz" err=<nil> mlog="/tmp/metadata-1567720190.log" planDir="/storage/metadata"
   time="2019-09-05T21:49:51Z" level=info msg="S3 upload finished `/storage/metadata/metadata-1567720190.gz` -> `metadata/zenko-west-1/metadata-1567720190.gz` Total: 4.74 KiB, Transferred: 4.74 KiB, Speed: 30.07 KiB/s " plan=metadata
   time="2019-09-05T21:49:51Z" level=info msg="On demand backup finished in 1.222549426s archive metadata-1567720190.gz size 4.9 kB" plan=metadata

Success/failure logs are sent via SMTP and/or Slack if notifications are enabled
(this feature remains in test).

The mongodump log is stored, along with the backup data (gzip archive), in the
/storage/metadata directory:

.. code::
   
   bash-4.4# ls -lh /storage/metadata/
   total 48
   -rw-r--r--    1 root     1000        4.7K Sep  5 21:45 metadata-1567719906.gz
   -rw-r--r--    1 root     1000         521 Sep  5 21:45 metadata-1567719906.log
   -rw-r--r--    1 root     1000        4.7K Sep  5 21:49 metadata-1567720190.gz
   -rw-r--r--    1 root     1000         521 Sep  5 21:49 metadata-1567720190.log
   -rw-r--r--    1 root     1000        4.8K Sep  5 21:51 metadata-1567720275.gz
   -rw-r--r--    1 root     1000         521 Sep  5 21:51 metadata-1567720275.log
   -rw-r--r--    1 root     1000        4.8K Sep  5 22:15 metadata-1567721706.gz
   -rw-r--r--    1 root     1000         522 Sep  5 22:15 metadata-1567721706.log
