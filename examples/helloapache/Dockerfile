FROM projectatomic/atomicapp:dev

MAINTAINER Aaron Weitekamp <aweiteka@redhat.com>

ADD /nulecule /Dockerfile README.md /application-entity/
ADD /graph /application-entity/graph

LABEL RUN docker run -it --rm --privileged --net=host -v `pwd`:/atomicapp -v /run:/run -v /:/host --name NAME -e NAME=NAME -e IMAGE=IMAGE IMAGE -v run /atomicapp
LABEL INSTALL docker run --rm -it --privileged -v /run:/run -v `pwd`:/atomicapp -e IMAGE=IMAGE -e NAME=NAME --name NAME IMAGE -v install --destination /atomicapp /application-entity
