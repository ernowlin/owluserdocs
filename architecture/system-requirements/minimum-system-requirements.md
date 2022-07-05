# Minimum System Requirements

## Hardware based on role&#x20;

Standalone, distributed, or fully-distributed.

* Please see [hardware sizing](hardware-sizing.md) for minimum resources for each component.

## Java version

* Oracle JDK version 1.8.0\_152.x
* Open JDK version 1.8.0.x

## Encryption

* Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction

## Postgres Version

* Collibra Data Quality comes prepackaged with version 11.4 of Postgres.
* Version 9.6.5 and above is supported if wanting to use an external metastore.

## User Privileges

* Installation is completed via tarball.
* You must be able to create directories, launch scripts, and start processes (java processes).
* SUDO is not required.
* ULIMIT settings of 4096 or higher
  * All owl services typically consume about 428 threads.
  * During each owlcheck about 400 additional threads are consumed.
  * Thus 4096 threads can allow for about 9 concurrent owlcheck jobs (on a standalone install). If more are needed plan accordingly.

## Planning the installation

It is always best to consult the Collibra Data Quality for more information about what options make the most sense for your environment.

1. Determine how we are planning to install CDQ (standalone or distributed) as shown in the Architecture section
2. Plan infrastructure, scale, and HA
3. Validate your system prereqs
4. Obtain the Packages from Owl

## Installation Packages/Files (BOM)

* demoscripts.tar.gz
* log4j\*
* owlcheck
* owl-core-2.1.0-jar-with-dependencies.jar
* owl-webapp-2.1.0.jar
* owl-agent-2.1.0.jar
* setup.sh
* owl-postgres.tar.gz
* notebooks.tar.gz
* owlmanage.sh

## Default Ports used by Collibra DQ

* 5432 – Postgres
* 9000 – Owl-web
