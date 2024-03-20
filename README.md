<configuration>

  <!-- Include parent configuration -->
  <include resource="parent-logback.xml"/>

  <!-- Define new file appender -->
  <appender name="SPECIAL_LOGGER" class="ch.qos.logback.core.rolling.RollingFileAppender">
    <file>path/to/your/special.log</file>
    <encoder>
      <pattern>%date %level [%thread] %logger{10} [%file:%line] %msg%n</pattern>
    </encoder>
    <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
      <fileNamePattern>path/to/your/special.%d{yyyy-MM-dd}.log</fileNamePattern>
      <maxHistory>30</maxHistory>
    </rollingPolicy>
  </appender>

  <!-- Define new logger -->
  <logger name="specialLogger" level="DEBUG" additivity="false">
    <appender-ref ref="SPECIAL_LOGGER"/>
  </logger>

</configuration>
