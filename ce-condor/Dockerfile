FROM opensciencegrid/software-base:fresh

RUN groupadd -g 2000 condor && useradd -u 2000 -g 2000 -s /sbin/nologin condor

RUN yum -y install  \
                   osg-ca-certs \
                   cilogon-openid-ca-cert && \
    yum -y install  \
                   condor \
                   redhat-lsb-core && \
    yum -y install osg-ce-condor

RUN yum -y update

RUN yum clean all

ADD condor.d/90_daemons.config /etc/condor/config.d/99_daemons.config

ADD osg.d/20-condor.ini /etc/osg/config.d/20-condor.ini

ADD cron.d/fetch-crl.cron /etc/cron.d/fetch-crl.cron

ADD supervisord.d/condor.conf /etc/supervisord.d/condor.conf
ADD supervisord.d/condor-ce.conf /etc/supervisord.d/condor-ce.conf

ADD mage-config.d/90_osg-configure.sh /etc/osg/image-config.d/90_osg-configure.sh 

# enables gratia
RUN touch /var/lock/subsys/gratia-probes-cron

