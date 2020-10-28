# OpenTelemetry auto instrucmentatio java + log4j sample

### Steps to run the example

1. wget https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/latest/download/opentelemetry-javaagent-all.jar

2. ./gradlew build

3. starting java app - with logging exporter

 
 ``` 
 java -javaagent:./opentelemetry-javaagent-all.jar \
 -Dotel.exporter=logging  \
 -jar -Dlogging.config="classpath:/log4j2.xml"  \
 build/libs/rest-service-0.0.1-SNAPSHOT.jar
 ```
 
4. starting java app - with jaeger exporter : 
 
 ```
 java -javaagent:./opentelemetry-javaagent-all.jar \
 -Dotel.exporter.jaeger.service.name=sample-app  \
 -Dotel.exporter=jaeger  \
 -jar -Dlogging.config="classpath:/log4j2.xml"  \
 build/libs/rest-service-0.0.1-SNAPSHOT.jar
 ```
5. open the url: http://localhost:8080/greeting and look at the console logs. The log enties will show traceId and spandId like this: [traceId=....] [spanId=....].

