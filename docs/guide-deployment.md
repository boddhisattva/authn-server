---
title: AuthN Deployment
tags:
  - guides
  - deployment
---

AuthN may be deployed to suit your needs. Currently it is provided in a Docker image, but as a Go
application it may be compiled for any target architecture and run as a daemon.

## Dependencies

AuthN requires:

* A SQL database (currently supports MySQL and Sqlite3) ([submit a request](https://github.com/keratin/authn-server/issues))
* A Redis server for session tokens, ephemeral data, and activity metrics.
* Network routing from your application's clients.
* Network routing to/from your application, for secure back-channel API communication.

## Deployment Strategy

1. Provision a server (or decide to colocate it on an existing server)
2. Deploy the code
3. Set environment variables to configure the database and other settings
4. Run migrations
5. Send traffic!

## Maximum Security

Ensure that all communication to AuthN happens with SSL.

Give AuthN its own dedicated SQL and Redis databases and be sure that all database backups are
strongly encrypted at rest. The credentials and accounts data encapsulated by AuthN should not be
necessary for data warehousing or business intelligence, so try to minimize their exposure.

## Related Guides

* [Deploying with Docker](guide-deploying_with_docker.md)
* [Integrating AuthN with an API Gateway](guide-integrating_authn_with_an_api_gateway.md)
