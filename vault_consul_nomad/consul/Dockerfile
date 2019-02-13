# base image
FROM alpine:3.7

# set consul version
ENV CONSUL_VERSION 1.4.2

# create a new directory
RUN mkdir /consul

# download dependencies
RUN apk --no-cache add \
      bash \
      ca-certificates \
      wget
	  
# download and set up consul
RUN wget --quiet --output-document=/tmp/consul.zip https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip && \
    unzip /tmp/consul.zip -d /consul && \
    rm -f /tmp/consul.zip && \
    chmod +x /consul

# update PATH
ENV PATH="PATH=$PATH:$PWD/consul"


# expose ports
EXPOSE 8400
EXPOSE 8500
EXPOSE 8600

# run consul
ENTRYPOINT ["consul"]