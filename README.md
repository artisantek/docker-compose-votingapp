Docker Compose Voting App
=========

A simple distributed application running across multiple Docker containers.

Run the following command inside the directory:
```
docker compose up -d
```
The app will be running at [hostip:5000], and the results will be at [hostip:5001].

Architecture
-----

<p align="center">
<img src="https://user-images.githubusercontent.com/113725746/206869022-b74f040a-47af-4f21-aceb-72c057840bfa.jpg" alt="architecture" width="500"/>
</p>

* A front-end web app in [Python](/vote) which lets you vote between two options
* A [Redis](https://hub.docker.com/_/redis/) queue which collects new votes
* A [Java](/worker) worker which consumes votes and stores them in…
* A [Postgres](https://hub.docker.com/_/postgres/) database backed by a Docker volume
* A [Node.js](/result) webapp which shows the results of the voting in real time


Notes
-----

The voting application only accepts one vote per client. It does not register votes if a vote has already been submitted from a client.

This isn't an example of a properly architected perfectly designed distributed app... it's just a simple 
example of the various types of pieces and languages you might see (queues, persistent data, etc), and how to 
deal with them in Docker at a basic level. 
