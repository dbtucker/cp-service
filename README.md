# cp-service
Service management scripts for Confluent Platform

Simple scripts to integrate the confluent platform services
(Kafka, Zookeeper, Schema Registry, REST interface) with the
O/S-level start-stop logic.   The scripts use the standard
upstart model (not systemctl), so as to remain consistent
between Ubuntu and CentOS/Redhat.

Install to /opt/confluent-*/initscripts and then create
symbolic links to those files from /etc/init.d

Initialize the service with
	chkconfig cp-<zk|broker|schema|rest>-service on

And then confirm with
	chkconfig --list

Confirm operation with
	/etc/init.d/cp-*-service start
		OR
	service cp-*-service start

NOTE: All services are run as the logical user that owns the 
service configuration file.   The side effect of this is that
if the service is run initially as one user and then the ownership
of $CONF_HOME/etc/<property-file> is changed, the service may NOT
start properly because the $CONF_HOME/logs/<log-file> cannot be
overwritten or the data files are not writable.

