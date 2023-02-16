# Описать создание Dockerfile для приложений.
# Описать docker-compose для запуска контейнеров.

FROM openjdk:11

WORKDIR /app1

COPY /dir_app1 .

ENV PORT 9001
ENV CONFIG_FILE_PATH conf/app1.conf
ENV JAVA_OPTS -Xms512m -Xmx1G

CMD nohup ./bin/app1 \
      -Dconfig.file=$CONFIG_FILE_PATH \
      -Dhttp.port=$PORT \
      -Dfile.encoding=UTF8 > app1.log 2>&1 &
