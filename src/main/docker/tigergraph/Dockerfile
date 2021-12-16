FROM docker.tigergraph.com/tigergraph:latest
USER tigergraph

WORKDIR /tmp
RUN curl -k -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.16.1-amd64.deb
RUN sudo dpkg -i filebeat-7.16.1-amd64.deb
COPY filebeat.yml /etc/filebeat/filebeat.yml

WORKDIR /home/tigergraph
ENTRYPOINT ["sudo","/bin/sh","-c","service ssh start && su - tigergraph bash -c '/home/tigergraph/tigergraph/app/cmd/gadmin start all'  && service filebeat start && tail -f /dev/null"]