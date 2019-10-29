Out-of-Band Updates
===================

Zenko depends on object storage metadata for its operation. When a new Zenko
location is configured, Zenko encounters a new object storage system. If Zenko
does not understand the location's namespace, Zenko creates a new Zenko
namespace and uses it to perform all of its data management tasks (metadata
search, replication, lifecycle transition and expiration). If Zenko recognizes
the existing namespace, it can ingest the existing namespace metadata, in a
process called an out-of-band update.

Transparent out-of-band updates are available for Scality's RING object storage
system via S3 Connector. Zenko communicates directly with the S3 Connector
namespace and replicates it natively. Zenko can also interoperate with RINGs
using the Scale-Out File System (SOFS) via the NFS protocol and with buckets
hosted by Amazon Web Services. For NFS and AWS data stores, Zenko downloads and
extrapolates metadata from the stores to create its own namespace, updates the
namespace in scheduled cron jobs, then acts on changes registered in this
virtual namespace.

When establishing a Zenko location for out-of-band updates, versioning must be
enabled. Out-of-band updates for S3C provide metrics; for NFS and AWS services,
metrics remain under development.
