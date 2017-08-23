Current hosting: Contigex and AWS.

## Contigex

mostly Rails apps and one NodeJS app.

* prx.org (Rails 2)
* count.prx.org (analytics for listening and viewing assets) (NodeJS)
* castle.prx.org (mysql, star schema, data mart: big database with API, data only for prx.org) (Rails 3)
* search.prx.org (Solr (old version))
* billboard (runs public radio player mobile app)
* networks (easy file transfer for journalism centers, et al)

## AWS

* fixer.prx.org (supports SubAuto) (Rails 3)
* big S3 bucket mirrored to regional FTP servers (read-only, pulled by stations)

DB
* V3 (mysql production prx.org)

Frontend
* publish
* beta
* play

API
* CMS
* ID
* Feeder
* Crier
* Castle^2
* alpha fixer