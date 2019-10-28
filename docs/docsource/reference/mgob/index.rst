MGOB
====

The kubectl command::

   $ kubectl get svc zenko-mgob

returns:

.. code:: sh

   NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)    AGE
   zenko-mgob   ClusterIP   None         <none>        8090/TCP   3d

.. note::

   Because the release name is "zenko", the service name is "zenko-mgob".

As indicated in the kubectl response, the MGOB service runs on port 8900 in the
Zenko context. It offers the following endpoints: 

.. tabularcolumns:: ll
.. table::

   +-----------------------------+-----------------------------------+
   | Endpoint                    | Function                          |
   +=============================+===================================+
   | ``zenko-mgob:8090/backup``  |                                   |
   +-----------------------------+-----------------------------------+
   | ``zenko-mgob:8090/debug``   | pprof endpoint                    |
   +-----------------------------+-----------------------------------+
   | ``zenko-mgob:8090/metrics`` | Prometheus endpoint               |
   +-----------------------------+-----------------------------------+
   | ``zenko-mgob:8090/status``  | Backup jobs status                |
   +-----------------------------+-----------------------------------+
   | ``zenko-mgob:8090/storage`` | File server                       |
   +-----------------------------+-----------------------------------+
   | ``zenko-mgob:8090/version`` | MGOB version and runtime info     |
   +-----------------------------+-----------------------------------+

These endpoints are described in the following sections.

.. toctree::
   :maxdepth: 1

   backup
   debug
   metrics
   status
   storage
   version   
