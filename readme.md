**Кейс – Разработчик (DevOps)**
**Вводная**

Написать service файлы для systemd.

**Описание**

Есть несколько приложений, которые выглядят примерно одинаково:

`.
└── /

├── bin/

│   ├── application_name

│   └── application_name.bat

├── conf/

│   ├── application.conf

│   └── params.conf

└── lib/

         ├── lib1.jar

         ├── lib2.jar

         └── libN.jar`

В приложении используются файлы конфигурации. В примере выше присутствует
константный файл конфигурации application.conf и файл params.conf. Файлы типа *.conf
являются HOCON файлами https://habr.com/ru/company/mailru/blog/306848/. application.conf -
описание конфигурации, который в себя импортирует params.conf - в этом файле
содержатся переменные, которые зависят от среды.
В качестве примера, для запуска приложения используется следующий скрипт:
`export PORT=&quot;9001&quot;

export CONFIG_FILE_PATH=&quot;conf/application.conf&quot;

export JAVA_OPTS=&quot;-Xms512m -Xmx1G&quot;

 
nohup ./bin/application_name \

     -Dconfig.file=$CONFIG_FILE_PATH \

     -Dhttp.port=$PORT \

     -Dfile.encoding=UTF8 &gt; application.log 2&gt;&amp;1 &amp;`

из примера видно, что переменная JAVA_OPTS применяется внутри скрипта старта
приложения `./bin/application_name`, а не при старте приложения.

**Задача**

Реализовать запуск 2 приложений app1, app2. При этом запуск app2 происходит только
после app1. И приложение app2 необходимо запустить в 2 экземплярах. 

**Задача**

Попробовать описать создание Dockerfile для описанных выше приложений.

**Задача**

Описать docker-compose для запуска контейнеров описанных выше.