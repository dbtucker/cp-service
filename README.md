# cp-service
Service management scripts for Confluent Platform

Simple scripts to integrate the confluent platform services
(Kafka, Zookeeper, Schema Registry, REST interface) with the
O/S-level start-stop logic.   The scripts use the standard
upstart model (not systemctl), so as to remain consistent
between Ubuntu and CentOS/Redhat.

