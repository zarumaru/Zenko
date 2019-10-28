On-Demand Backup
~~~~~~~~~~~~~~~~

Request
^^^^^^^

POST ``zenko-mgob:8090/backup/:planID``

Sample
++++++

.. code:: bash

      curl -X POST http://zenko-mgob:8090/backup/metadata

Response
^^^^^^^^

Sample
++++++

.. code:: json

   {
     "plan": "metadata",
     "file": "metadata-1567721706.gz",
     "duration": "1.264375987s",
     "size": "4.9 kB",
     "timestamp": "2019-09-05T22:15:06.529181117Z"
   }
