# Use Ubuntu as base image
FROM ubuntu:20.04

LABEL Eric Wang

# Download and install xidel.
# Parse html with xpath to download server. Used in getbedrockserver.sh
#ADD https://github.com/benibela/xidel/releases/download/Xidel_0.9.8/xidel_0.9.8-1_amd64.deb /
#RUN dpkg -i /xidel_0.9.8-1_amd64.deb

# Install necessary packages
RUN apt-get update && apt-get install -y --no-install-recommends unzip apt-utils libssl1.1 curl ca-certificates
#wget apt-utils libssl1.1 ca-certificates curl

# Install time zone package
RUN DEBIAN_FRONTEND=noninteractive TZ=Asia/Taipei apt-get -y install tzdata

# Expose minecraft bedrock port IPv4
EXPOSE 19132/tcp
EXPOSE 19132/udp
# Expose minecraft bedrock port IPv6
EXPOSE 19133/tcp
EXPOSE 19133/udp


# Set workdir
WORKDIR /bedrock-server

# Download bedrock server zip
#COPY ./getbedrockserver.sh /
#RUN chmod +x /getbedrockserver.sh
#RUN /getbedrockserver.sh
ADD https://minecraft.azureedge.net/bin-linux/bedrock-server-1.19.20.02.zip /bedrock-server/
RUN unzip /bedrock-server/bedrock-server-1.19.20.02.zip -d /bedrock-server
RUN rm /bedrock-server/bedrock-server-1.19.20.02.zip
# Unzip to workdir
#RUN unzip bedrock-server-ubuntu.zip

# Set env path
ENV LD_LIBRARY_PATH=/bedrock-server

# set permission
RUN chmod +x bedrock_server

# Start server
CMD ["/bedrock-server/bedrock_server"]


