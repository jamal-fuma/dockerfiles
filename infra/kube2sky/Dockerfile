FROM tonnerre/ancientsolutions-base:latest
MAINTAINER Tonnerre LOMBARD <tonnerre@ancient-solutions.com>

RUN apt-get -q -y -o Dpkg::Options::=--force-confdef -o Dpkg::Options::=--force-confold --purge install ca-certificates ancient-ca
RUN ln /etc/ancientca/services/cacert.pem /etc/ssl/certs/ancientca-services.crt
RUN ln -s ancientca-services.crt /etc/ssl/certs/$(openssl x509 -noout -hash -in /etc/ssl/certs/ancientca-services.crt).0
RUN ln /etc/ancientca/root/cacert.pem /etc/ssl/certs/ancientca-root.crt
RUN ln -s ancientca-root.crt /etc/ssl/certs/$(openssl x509 -noout -hash -in /etc/ssl/certs/ancientca-root.crt).0
RUN /usr/sbin/update-ca-certificates

ADD kube2sky kube2sky

ENTRYPOINT ["/kube2sky"]
