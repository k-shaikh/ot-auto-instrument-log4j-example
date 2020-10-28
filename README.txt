Sample showing OpenTelemetry auto instrucmentation for java and injection of trace and span into log4j MDC

Steps to run the example

* wget https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/latest/download/opentelemetry-javaagent-all.jar
* ./gradlew build
* testing with logging exporter: java -javaagent:./opentelemetry-javaagent-all.jar -Dotel.exporter=logging  -jar -Dlogging.config="classpath:/log4j2.xml"  build/libs/rest-service-0.0.1-SNAPSHOT.jar
* testing with jaeger: ava -javaagent:./opentelemetry-javaagent-all.jar -Dotel.exporter.jaeger.service.name=sample-app  -Dotel.exporter=jaeger  -jar -Dlogging.config="classpath:/log4j2.xml"  build/libs/rest-service-0.0.1-SNAPSHOT.jar
* open the url: http://localhost:8080/greeting and look at the console logs. The log enties will show traceId and spandId like this: [traceId=....] [spanId=....].

