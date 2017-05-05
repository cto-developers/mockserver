#
# MockServer Dockerfile
#
# https://github.com/jamesdbloom/mockserver
# http://www.mock-server.com
#

# pull base image
FROM java

# maintainer details
MAINTAINER Daniel Ceballos "daniel.ceballos@cto-global.org"

# download MockServer
RUN mkdir -p /opt/mockserver
COPY mockserver-netty/target/mockserver-netty-3.10.8-SNAPSHOT-jar-with-dependencies.jar /opt/mockserver/mockserver-netty-jar-with-dependencies.jar
COPY docker/run_mockserver.sh /opt/mockserver/run_mockserver.sh
COPY mockserver-core/src/main/resources/org/mockserver/socket/CertificateAuthorityCertificate.pem /opt/mockserver/CertificateAuthorityCertificate.pem
RUN chmod +x /opt/mockserver/run_mockserver.sh

# set working directory
WORKDIR /opt/mockserver

# expose ports.
EXPOSE 1080 1090

# define default command.
CMD ["/opt/mockserver/run_mockserver.sh", "-logLevel", "INFO", "-serverPort", "1080", "-proxyPort", "1090", "-corsHeaders", "\"x-xsrf-token, x-session-token\""]
