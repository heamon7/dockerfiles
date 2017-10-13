FROM ubuntu:16.04
MAINTAINER heamon7 <heamon7@gmail.com>
ENV VERSION=1.0.1

RUN apt-get update -qq
RUN apt-get install python-software-properties -y -qq

RUN mkdir -p /script
WORKDIR /script
ADD setup7.x.sh /script/
RUN chmod a+x setup7.x.sh
RUN ./setup7.x.sh && rm setup7.x.sh

# install Node.js
RUN apt-get update -qq
RUN apt-get install build-essential nodejs -y -qq
RUN npm install -g node-gyp

# install git
RUN apt-get -y install git

# install wiki.js
RUN mkdir -p /wiki
WORKDIR /wiki
RUN curl -L -s -S https://github.com/Requarks/wiki/releases/download/v$VERSION/wiki-js.tar.gz | tar xz -C .
RUN npm install --only=production

EXPOSE 80 3000

CMD ["node", "wiki", "configure"]