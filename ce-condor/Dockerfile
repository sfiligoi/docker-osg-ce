FROM sfiligoi/osg-ce:base

RUN yum -y install  \
                   condor \
                   redhat-lsb-core && \
    yum -y install osg-ce-condor

RUN yum -y update

RUN yum clean all

ADD osg.d/20-condor.ini /etc/osg/config.d/20-condor.ini

ADD condor.d/90_daemons.config /etc/condor/config.d/90_daemons.config
ADD supervisord.d/condor.conf /etc/supervisord.d/condor.conf

