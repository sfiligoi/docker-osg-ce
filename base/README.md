# docker-osg-ce/base Repository

This repository contains the base Dockerfile necessary to build
OSG CE images.

# Usage

While this image is not suitable to be used on its own, the following step will be necessary in any inherited image.

Required files to be injected in the image at instantiation time:
* /etc/grid-security/hostcert.pem - Node specific
* /etc/grid-security/hostkey.pem - Associated with hostcer, must be readable by root only
* /etc/osg/config.d/40-siteinfo.ini - Description of the CE. See [OSG CE docvumentation](https://opensciencegrid.org/docs/compute-element/htcondor-ce-overview/) for more details.
* /etc/osg/config.d/30-gip.ini - Description of the compute cluster. See [OSG CE docvumentation](https://opensciencegrid.org/docs/compute-element/htcondor-ce-overview/) for more details.

Optionally, put in place:
* /etc/grid-security/grid-mapfile - List of local admins. See [OSG CE docvumentation](https://opensciencegrid.org/docs/compute-element/htcondor-ce-overview/) for more details. 

The following areas should be persistent across container restarts:
* /var/lib/condor-ce - Base directory of where the CE keeps its status. Must be owner by the condor user.
* /var/lib/condor-ce/spool - As above; may be on the same or on a different partition.
* /var/lib/condor-ce/execute - As above; may be on the same or on a different partition.

Finally, the CE requires proper Linux accounts to exist for all the supported user communities.
The accounts should be configured using the standard Linux commands (e.g. useradd) during container startup by a file located in:
* /etc/osg/image-config.d/
e.g.
* /etc/osg/image-config.d/20_create.account.sh
Please make sure the UID and GID of such accounts are persistent across container restarts.

# Image repository

The images are being build and are availble on [DockerHub as sfiligoi/osg-ce:base](https://cloud.docker.com/u/sfiligoi/repository/docker/sfiligoi/osg-ce).

