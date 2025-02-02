Example Voting App
=========

A simple distributed application running across multiple Docker containers.

Forked Version for Class Lab
---------------
This project is a fork of the [Example Voting App by KodeKloudHub](https://github.com/kodekloudhub/example-voting-app). It has been adapted for use in a Kubernetes hands-on lab as part of a DevOps course.

The original README with installation and running instructions can be found in the [kodekloudhub/example-voting-app](https://github.com/kodekloudhub/example-voting-app).

Architecture
-----

![Architecture diagram](architecture.png)

* A front-end web app in [Python](/vote) or [ASP.NET Core](/vote/dotnet) which lets you vote between two options
* A [Redis](https://hub.docker.com/_/redis/) or [NATS](https://hub.docker.com/_/nats/) queue which collects new votes
* A [.NET Core](/worker/src/Worker), [Java](/worker/src/main) or [.NET Core 2.1](/worker/dotnet) worker which consumes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/) or [TiDB](https://hub.docker.com/r/dockersamples/tidb/tags/) database backed by a Docker volume
* A [Node.js](/result) or [ASP.NET Core SignalR](/result/dotnet) webapp which shows the results of the voting in real time

Note
----

The voting application only accepts one vote per client. It does not register votes if a vote has already been submitted from a client.
