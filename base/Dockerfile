FROM opensciencegrid/software-base:3.5-el7-release

# Fix condor UID to allow for persistency
RUN groupadd -g 2000 condor && useradd -u 2000 -g 2000 -s /sbin/nologin condor

RUN yum -y install  \
                   osg-ca-certs \
                   cilogon-openid-ca-cert && \
    yum -y install osg-ce

RUN yum -y update

RUN yum clean all

ADD cron.d/fetch-crl.cron /etc/cron.d/fetch-crl.cron

ADD supervisord.d/condor-ce.conf /etc/supervisord.d/condor-ce.conf

ADD image-config.d/90_osg-configure.sh /etc/osg/image-config.d/90_osg-configure.sh 

# enables gratia
RUN touch /var/lock/subsys/gratia-probes-cron

