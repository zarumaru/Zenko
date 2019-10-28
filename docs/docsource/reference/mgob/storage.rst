Storage
=======

There are two options for restoring from a local backup:

*  Use mongorestore against an archive on the server: 

   #. Browse {{release-name}}-mgob-0:8090/storage to identify the backup to
      restore.

   #. Using curl, log in to your MongoDB server and download the archive.

   #. Restore the backup using ``mongorestore``. 

      .. code:: bash

         $ curl -o /tmp/metadata-1567719906.gz http://zenko-mgob:8090/storage/metadata/ metadata-1567719906.gz

         $ mongorestore --gzip --archive=/tmp/mongo-test-1494056760.gz --drop

*  Use mongorestore to restore from within an MGOB container:

   #. From within an mgob container, exec into mgob and identify the backup to
      restore.

   #. Use mongorestore to connect to your MongoDB server.

      .. code:: bash

         $ kubectl exec -it {{release-name}}-mgob-0 bash

         $ ls /storage/meatadata

         $ mongorestore --gzip --archive=/storage/metadata/metadata-1567719906.gz --host mongohost:27017 --drop
