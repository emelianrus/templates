# base image
FROM ubuntu:xenial

# set nomad version
ENV NOMAD_VERSION 0.8.7

# create a new directory
RUN mkdir /nomad

# download dependencies

RUN apt-get update

RUN apt-get install -y \
      bash \
      ca-certificates \
      wget \
      unzip



# download and set up nomad
RUN wget --quiet --output-document=/tmp/nomad.zip https://releases.hashicorp.com/nomad/${NOMAD_VERSION}/nomad_${NOMAD_VERSION}_linux_amd64.zip   && \
    unzip /tmp/nomad.zip -d /nomad && \
    rm -f /tmp/nomad.zip && \
    chmod +x /nomad

# update PATH
ENV PATH="PATH=$PATH:$PWD/nomad"

# expose port 8200
EXPOSE 4646
EXPOSE 4647
EXPOSE 4648


# run nomad
ENTRYPOINT ["nomad"]