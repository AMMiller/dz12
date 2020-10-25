FROM maven:slim

RUN apt update && \
    apt install -y git

WORKDIR /var/lib/maven/app

RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample.git && \ 
    sed -i 's/source>1.6</source>1.8</' App42PaaS-Java-MySQL-Sample/pom.xml && \
    sed -i 's/target>1.6</target>1.8</' App42PaaS-Java-MySQL-Sample/pom.xml

CMD mvn package -f App42PaaS-Java-MySQL-Sample/pom.xml && \
    mv $(ls App42PaaS-Java-MySQL-Sample/target/*.war | sed 's/.war//') ROOT && \
    echo "app42.paas.db.username = $MYSQL_USER" > ROOT/Config.properties && \
    echo "app42.paas.db.port = $MYSQL_PORT" >> ROOT/Config.properties && \
    echo "app42.paas.db.password = $MYSQL_PASS" >> ROOT/Config.properties && \
    echo "app42.paas.db.ip = $MYSQL_HOST" >> ROOT/Config.properties && \
    echo "app42.paas.db.name = $MYSQL_DB" >> ROOT/Config.properties && \
    rm -rf App42PaaS-Java-MySQL-Sample
