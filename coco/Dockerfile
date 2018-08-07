FROM mapsic/python:v3.6.1

ENV coco_version=1.4.0
 
COPY run.sh /usr/local/bin/run.sh

RUN wget https://github.com/jumpserver/coco/archive/${coco_version}.zip -O /opt/coco.zip \
    && unzip coco.zip \
    && ln -sv coco-${coco_version} coco     \
    && rm -rf /opt/coco.zip                 \
    && source /opt/py3/bin/activate         \ 
    && yum -y  install $(cat /opt/coco/requirements/rpm_requirements.txt) \
    && pip install -r /opt/coco/requirements/requirements.txt  \
    && wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.2.1/dumb-init_1.2.1_amd64 \
    && chmod a+x /usr/local/bin/dumb-init \
    && chmod a+x /usr/local/bin/run.sh

EXPOSE 2222 5000

ENTRYPOINT ["/usr/local/bin/dumb-init", "--"]

CMD ["/usr/local/bin/run.sh"]
