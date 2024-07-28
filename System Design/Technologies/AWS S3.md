[Source](https://www.stitchdata.com/resources/aws-s3)

#### Overview
- Amazon Simple Storage Service

#### Storage
- AWS S3 is a [[key-value store]]. 
- Uploaded objects are referenced by a unique key, which can be any string.
- S3 is capable of storing diverse and generally unstructured data, but it's also suited for hierarchical data and all kinds of structured information. 

#### Buckets
- Amazon S3 objects are organised in buckets. 
- Buckets are the main containers in S3, and every object must be stored in one. 
- All of S3’s main features, such as the interfaces and APIs, can act either on buckets or individual objects.
- When users upload data, they create a bucket with a name first, then move however many objects they need into it. 
- AWS S3 uses an **Object Key**, along with a version identifier, to uniquely identify objects in a bucket. This helps users to organise data.

#### APIs and integrations
- Exposes REST API to stored data
- URLs can point directly to stored resources/objects

#### Use Cases
###### Data lake creation:
- An S3 data lake enables users to unlock insights to maximise the full value of their data. This is achieved by running applications involving big data analytics, high performance computing (HPC), artificial intelligence (AI), and machine learning (ML).
###### Critical data backup and restoration
- Robust replication features make it easier for organisations to meet **Recovery Time Objectives (RTO)** and **Recovery Point Objectives (RPO)** in the event of a disaster. Backup features also support compliance measures.
###### Low-cost data archiving. 
- Moving data archives to certain levels of AWS S3 service, such as the Glacier storage classes, allow businesses to save money and streamline operations while still keeping data available for generating additional insights.
###### Operation of cloud-native applications. 
- Developers in particular will enjoy the ability to build robust, speedy mobile and web-based cloud-native apps that are configured to be highly available and scale automatically.

#### Real World Examples
- Companies like Airbnb, Netflix, Pinterest, and Reddit use S3 to host their web content, images, archives, backups of on-premises data for disaster recovery, and systems of record.
- Old orders on Amazon.com (more than a year old) are apparently archived to Amazon S3 since they are read-only (no returns, no changes).