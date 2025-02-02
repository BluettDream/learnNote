log4j2 config file

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="WARN" monitorInterval="15">
    <properties>
        <property name="LOG_HOME">logs</property>
        <property name="PATTERN_FORMAT">%d{HH:mm:ss.SSS} [%t] [%-5level] %c.%M(%L) - %msg%n</property>
    </properties>

    <Appenders>
        <Console name="Console" target="SYSTEM_OUT">
            <PatternLayout pattern="${PATTERN_FORMAT}" />
            <ThresholdFilter level="DEBUG" onMatch="ACCEPT" onMismatch="NEUTRAL" />
        </Console>

        <RollingRandomAccessFile name="DebugFile"
                                 fileName="${LOG_HOME}/debug.log"
                                 filePattern="${LOG_HOME}/$${date:yyyy-MM-dd}/debug-%d{yyyy-MM-dd}-%i.log.zip">
            <Filters>
                <ThresholdFilter level="INFO" onMatch="DENY" onMismatch="NEUTRAL" />
                <ThresholdFilter level="DEBUG" onMatch="ACCEPT" onMismatch="DENY" />
            </Filters>
            <PatternLayout pattern="${PATTERN_FORMAT}" />
            <Policies>
                <TimeBasedTriggeringPolicy />
                <SizeBasedTriggeringPolicy size="15 MB" />
            </Policies>
            <DefaultRolloverStrategy max="20" >
                <Delete basePath="${LOG_HOME}/" maxDepth="5">
                    <IfFileName glob="*debug*.log.zip"/>
                </Delete>
            </DefaultRolloverStrategy>
        </RollingRandomAccessFile>

        <RollingRandomAccessFile name="InfoFile"
                                 fileName="${LOG_HOME}/info.log"
                                 filePattern="${LOG_HOME}/$${date:yyyy-MM-dd}/info-%d{yyyy-MM-dd}-%i.log.zip">
            <Filters>
                <ThresholdFilter level="WARN" onMatch="DENY" onMismatch="NEUTRAL" />
                <ThresholdFilter level="INFO" onMatch="ACCEPT" onMismatch="DENY" />
            </Filters>
            <PatternLayout pattern="${PATTERN_FORMAT}" />
            <Policies>
                <TimeBasedTriggeringPolicy />
                <SizeBasedTriggeringPolicy size="15 MB" />
            </Policies>
            <DefaultRolloverStrategy max="20" >
                <Delete basePath="${LOG_HOME}/" maxDepth="5">
                    <IfFileName glob="*info*.log.zip"/>
                </Delete>
            </DefaultRolloverStrategy>
        </RollingRandomAccessFile>

        <RollingRandomAccessFile name="ErrorFile"
                                 fileName="${LOG_HOME}/error.log"
                                 filePattern="${LOG_HOME}/$${date:yyyy-MM-dd}/error-%d{yyyy-MM-dd}-%i.log.zip">
            <Filters>
                <ThresholdFilter level="FATAL" onMatch="DENY" onMismatch="NEUTRAL" />
                <ThresholdFilter level="WARN" onMatch="ACCEPT" onMismatch="DENY" />
            </Filters>
            <PatternLayout pattern="${PATTERN_FORMAT}" />
            <Policies>
                <TimeBasedTriggeringPolicy />
                <SizeBasedTriggeringPolicy size="10 MB" />
            </Policies>
            <DefaultRolloverStrategy max="15" >
                <Delete basePath="${LOG_HOME}/" maxDepth="5">
                    <IfFileName glob="*error*.log.zip"/>
                </Delete>
            </DefaultRolloverStrategy>
        </RollingRandomAccessFile>

        <RollingRandomAccessFile name="FatalFile"
                                 fileName="${LOG_HOME}/fatal.log"
                                 filePattern="${LOG_HOME}/$${date:yyyy-MM}/fatal-%d{yyyy-MM-dd}-%i.log.zip">
            <Filters>
                <ThresholdFilter level="FATAL" onMatch="ACCEPT" onMismatch="DENY" />
            </Filters>
            <PatternLayout pattern="${PATTERN_FORMAT}" />
            <Policies>
                <TimeBasedTriggeringPolicy />
                <SizeBasedTriggeringPolicy size="5 MB" />
            </Policies>
            <DefaultRolloverStrategy max="5" >
                <Delete basePath="${LOG_HOME}/" maxDepth="5">
                    <IfFileName glob="*fatal*.log.zip"/>
                </Delete>
            </DefaultRolloverStrategy>
        </RollingRandomAccessFile>
    </Appenders>

    <Loggers>
        <Logger name="org.apache" level="ERROR"/>
        <Logger name="org.mybatis" level="DEBUG"/>

        <Root level="INFO">
            <AppenderRef ref="Console" />
            <AppenderRef ref="DebugFile"/>
            <AppenderRef ref="InfoFile" />
            <AppenderRef ref="ErrorFile" />
            <AppenderRef ref="FatalFile" />
        </Root>
    </Loggers>
</Configuration>
```

log4j2 pattern format [website](https://logging.apache.org/log4j/2.x/manual/pattern-layout.html)