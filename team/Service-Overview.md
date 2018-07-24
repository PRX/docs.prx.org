This is high-level overview of applications and services that PRX is currently maintaining. 

# www.prx.org

[Proxy](https://github.com/prx/proxy.prx.org) that directs to exchange.prx.org or corporate.prx.org.

# corporate.prx.org

Squarespace site for company information.

# exchange.prx.org (version 3)

Version 3 of prx.org is a **Rails 2** application that runs on **PRX01** and **PRX04** hosted with **Contegix**. It runs off a MySQL database that is also hosted on **PRX01**, which is replicated on **PRX04** and **AWS RDS**.

Amazon **S3** is used to for user audio (and some other assets, like user images). **CloudFront** is used as a CDN for static site assets, like CSS and Javascript. **SQS** is used for queueing background tasks.

The prx.org v3 Rails app relies on **Fixer** for a number of things. Jobs are sent to Fixer to validate and encode user audio. Sub-auto delivery scheduling is handled by v3, but the deliveries themselves (pushing to stations' FTP servers) are processes by Fixer. 

# publish.prx.org

The version 4 of prx.org is a frontend-only **AngularJS** app. During deployment it is compiled down to files which can be served statically. The compilation and hosting are both handled by **PRX04** though **Contegix**.

The frontend relies on several other services, including: **cms.prx.org**, **id.prx.org**, and **upload.prx.org**.

# beta.prx.org

**AngularJS** app that will be replaced by **listen.prx.org**.

# cms.prx.org

cms.prx.org is the primary API for PRX user content. It is used to power **prx.org (v4)**, and integrates with **id.prx.org**, **feeder.prx.org**, and **fixer.prx.org** to handle various secondary functions.

CMS is **Rails 4** app that runs on **AWS ECS**. It shares a **MySQL** database with exchange.prx.org, but is currently in read-only mode running off the **AWS RDS** replication.

# id.prx.org

All aspects of authentication and authorization across PRX properties are being moved into the id.prx.org service. It is based on signed **JSON Web Tokens** that encapsulate various claims about users' abilities in a given app for a given resource.

The service is a **Rails 4** app that runs on **AWS ECS**.

# upload.prx.org

User content uploaded to **S3** from the **v4** frontend is cryptographically signed so that AWS will accept the upload. The service that does the signing is built using **API Gateway** and **AWS Lambda**. 

# Fixer

http://fixer.prx.org/

Fixer is a media processing application used by several other PRX services. **prx.org (v3)** and **cms.prx.org** are the primary utilizers. Mainly it is used for encoding user audio submitted to prx.org. This is done asynchronously, using callbacks. Fixer is able to pull in data from a number of common sources (S3, HTTP, etc). It also handles push delivery for Subauto via FTP.

Fixer is hosted on **EC2** and is designed to scale up with demand by launching additional workers that are managed by a master controller.

# Subauto

Subauto encompasses services provided by several other applications. Billing and management is handled by prx.org (v3), delivery by Fixer, etc. **FTP Pull** servers (that stations can pull files from) are run on **EC2**, and mirror **S3** buckets; the use the prxtransfer.org domain. **Chef** is also running on **EC2** which provides some authentication for the FTP servers.

# Feeder

Feeder extends the ability of **cms.prx.org** to provide support for podcast-specific metadata, as well as generates podcast feeds for podcast versions of *series* in the PRX marketplace.

Feeder watches for changes in data through **SNS**/**SQS**, and updates feeds as necessary when underlying data changes in either the CMS or Feeder itself.

It is a **Rails 4** application.

*Currently a work-in-progress; hosting details will be added later.*


