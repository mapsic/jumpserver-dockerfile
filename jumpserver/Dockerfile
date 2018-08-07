FROM mapsic/python:v3.6.1

ENV jms_version=1.4.0

RUN source /opt/py3/bin/activate     \    
    && wget https://github.com/jumpserver/jumpserver/archive/${jms_version}.zip  -O /opt/jumpserver.zip  \                                  
    && unzip jumpserver.zip               \          
    && ln -sv jumpserver-${jms_version} jumpserver   \   
    && yum -y install $(cat /opt/jumpserver/requirements/rpm_requirements.txt)  \
    && rm -rf /var/cache/yum/*                    \
    && rm -rf /opt/jumpserver.zip                 \
    && pip install -r /opt/jumpserver/requirements/requirements.txt 

EXPOSE 8080

CMD source /opt/py3/bin/activate && cd /opt/jumpserver/utils && sh make_migrations.sh && cd .. && python run_server.py
