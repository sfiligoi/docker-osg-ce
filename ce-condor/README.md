# docker-osg-ce/ce-condor Repository

This repository contains the Dockerfile necessary to build
OSG HTCondor CE image.

# Usage

First, make sure you follow the usage instructions from [the base image](../base/).

The additional steps are as follows.

Properly configure ithe HTCondor schedd. 
The right configuration is site specific, but the files should be located in:
* /etc/condor/config.d/

e.g.
* /etc/condor/config.d/98_security.config

See [HTCondor documentation](http://research.cs.wisc.edu/htcondor/manual/) for more details.


The following areas should be persistent across container restarts:
* /var/lib/condor - Base directory of where HTCondor keeps its status. Must be owner by the condor user.
* /var/lib/condor/spool - As above; may be on the same or on a different partition.


# Image repository

The images are being build and are availble on [DockerHub as sfiligoi/osg-ce:ce-condor](https://cloud.docker.com/u/sfiligoi/repository/docker/sfiligoi/osg-ce).

