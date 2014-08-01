docker-mesos-marathon
=====================

Usage 

* Create `supervisord.conf` file
```
[supervisord]
nodaemon=true

[program:mesos]
command=mesos-master --work_dir=./ --zk=zk://zookeeper.tapcat:2181/mesosphere --quorum=1

[program:marathon]
command=/bin/bash -c "/marathon-0.6.1/bin/start --master zk://zookeeper.tapcat:2181/mesosphere --zk zk://zookeeper.tapcat:2181/marathon"
```
* Run Docker container
```
docker run --name marathon.docker -d -v ~/mesosphere/supervisord.conf:/etc/supervisor/conf.d/supervisord.conf:ro borov/mesosphere
```
