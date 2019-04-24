HA PostgreSQL cluster configuration
=========

HA PostgreSQL cluster configuration example (PostgreSQL, Patroni, etcd and HAProxy with Keepalived).

Description
------------

The configuration example consists of 8 servers in total:

1. server50 (192.168.6.50) - MASTER HAProxy server 

2. server51 (192.168.6.51) - BACKUP HAProxy server

*Keepalived is configured on both HAProxy servers and the virtual ip address 192.168.6.60 is used as the frontend listening on port 5432.

3. server10 (192.168.6.10) - PostgreSQL and Patroni

4. server11 (192.168.6.11) - PostgreSQL and Patroni

5. server12 (192.168.6.12) - PostgreSQL and Patroni

*The replication is configured using Postgres' asynchronous streaming replication and Patronis API listens on port 8008 (https) using basic username/password authentication.

6. server40 (192.168.6.40) - etcd

7. server41 (192.168.6.41) - etcd

8. server42 (192.168.6.42) - etcd

*etcd is used as the distributed key-value store and listens on port 2379 for client connections and port 2380 for peer connections. Both ports are configured using Two-way SSL (Mutual Authentication).

Since this is only a test/demo example, all certificates (including private keys) are available for download.

Supported Systems
------------

Tested on CentOS 7.6.1810 on the following versions:

PostgreSQL 10.7

Patroni 1.5.6

etcd 3.3.11

HAProxy 1.5.18

Keepalived 1.3.5

