# Awesome Observability with stars

Monitoring as defined by the Oxford dictionary is to "Observe and check the progress or quality of (something) over a period of time; keep under systematic review".

For systems monitoring that means being able to give an overview over the state of a system by exposing key metrics about the systems. The monitoring can be implemented in different ways:

* one can push metrics from a service,
* pull metrics from it or
* use a combined hybrid approach

Furthermore, the concept of **observability** can be seen a superset of monitoring where it is a part of giving visibility into the system. Providing the  ability to reason about the system health in a better way.

It can be said to  consist of three parts:

* The **event logs** (can be in different forms, plain text, structured or binary and is in general about having a log about what happened at a certain time),
* The **metrics** (measurement over time, for example number of failed requests) and
* The **tracing** (represent related and distributed events together as a request flows through a system)

> **Metrics**, **Logs** and **Traces**: The Golden Triangle of Observability in Monitoring

This repo is not only for monitoring. As said Adrian Cole's in the talk about "[Observability 3 Ways](https://www.youtube.com/watch?v=juP9VApKy_I)" we are going to focus on the three types of systems necessaries to understand how your applications behave: Logging, Metrics & Tracing.

## Contents

* [1. Best Practices](#1-best-practices)
* [2. General Tools](#2-general-tools)
* [3. Collect](#3-collect)
* [4. Load Generators and Synthetic Traffic](#4-load-generators-and-synthetic-traffic)
* [5. Transport](#5-transport)
* [6. Collector](#6-collector)
* [7. Storage](#7-storage)
* [8. Visualization](#8-visualization)
* [9. Processing and Analyze and Act](#9-processing-and-analyze-and-act)
* [10. LLM & AI Observability](#10-llm--ai-observability)
* [11. GPU Observability](#11-gpu-observability)
* [12. Application Performance Monitoring Solutions (APM)](#12-application-performance-monitoring-solutions-apm)
* [13. Service Mesh](#13-service-mesh)
* [14. Observability as a Service](#14-observability-as-a-service)
* [15. Examples and Sandboxes](#15-examples-and-sandboxes)
* [16. References](#16-references)
* [17. License](#17-license)
* [18. Contributing](#18-contributing)

## 1. Best Practices

* [Best practices for monitoring cloud applications](https://docs.microsoft.com/en-us/azure/architecture/best-practices/monitoring)
* [The Three Pillars of Observability](https://learning.oreilly.com/library/view/distributed-systems-observability/9781492033431/ch04.html)

## 2. General Tools

Before to start with huge observability solution. If you just need to control some application aspects, visualize how is working your system, or just identify a problem, may be usefull start with one, or a collection application, that help you to get this information in a **easy** and **cheap** way.

Additional to this, start with tools to get information about your system to determine if it's working well, can help you to define the final stack if you want to install a corporative solution to any project. I know some stories abot people that install, configure and even evolution some monitoring tools as a corporative solution, an when the solution is in production, they realize that the tools don't cover all the necessaries to control their applications :-D

Following you can see an interesting post from Netflix writteb by [Brendan Gregg](http://www.brendangregg.com/) that show this very clear.

<https://netflixtechblog.com/linux-performance-analysis-in-60-000-milliseconds-accc10403c55>

In the article you can see how with a few tools and in a short time, you can get a lot of information about your system ;-)

```
 $ uptime
 $ dmesg | tail
 $ vmstat 1
 $ mpstat -P ALL 1
 $ pidstat 1
 $ iostat -xz 1
 $ free -m
 $ sar -n DEV 1
 $ sar -n TCP,ETCP 1
 $ top
```

There are many more commands and methodologies you can apply to drill deeper.

## 3. Collect

Get any data – metrics, events, logs, traces – from everywhere – systems, sensors, queues, databases and networks.

### Metrics

* [cAdvisor](https://github.com/google/cadvisor) ⭐ 19,393 | 🐛 63 | 🌐 Go | 📅 2026-09-02 - Container Advisor that provides container users an understanding of the resource usage and performance characteristics of their running containers.
* [ctop](https://github.com/bcicen/ctop) ⭐ 17,834 | 🐛 120 | 🌐 Go | 📅 2024-07-08 - Top-like interface for container metrics.
* [Node-exporter](https://github.com/prometheus/node_exporter) ⭐ 13,751 | 🐛 304 | 🌐 Go | 📅 2026-09-02 - Prometheus stack, Exporter for machine metrics.
* [Kuberhealthy](https://github.com/kuberhealthy/kuberhealthy) ⭐ 2,266 | 🐛 5 | 🌐 Go | 📅 2026-09-01 - Kubernetes operator for synthetic monitoring and continuous process verification.
* [sls-dev-tools](https://github.com/Theodo-UK/sls-dev-tools) ⭐ 870 | 🐛 62 | 🌐 JavaScript | 📅 2023-04-25 - The Developer Tools for the Serverless World - think Chrome Dev Tools but for Serverless.
* [ingraind](https://github.com/foniod/foniod) ⚠️ Archived - Security monitoring agent built around RedBPF for complex containerized environments and endpoints.
* [SSL Certificate Monitor](https://github.com/brancogao/ssl-certificate-monitor) ⭐ 15 | 🐛 0 | 🌐 TypeScript | 📅 2026-02-18 - Open-source SSL/TLS certificate expiry monitoring tool with email alerts for observability of certificate health.
* [DNS Propagation Checker](https://github.com/brancogao/dns-propagation-checker) ⭐ 1 | 🐛 0 | 🌐 TypeScript | 📅 2026-02-18 - Open-source DNS propagation monitoring tool with global DNS server coverage for DNS observability.
* [Opentelemetry](https://opentelemetry.io/) - Integrated set of APIs and libraries as well as a collection mechanism via an agent and collector.
* [top](https://www.booleanworld.com/guide-linux-top-command/) - Allows users to monitor processes and system resource usage on Linux. It is one of the most useful tools in a sysadmin's toolbox, and it comes pre-installed on every distribution.
* [htop](https://support.cloudways.com/system-monitoring-using-htop-command/) - Command line utility that allows you to interactively monitor your system's vital resources or server's processes in real time.
* [OpenCensus](https://opencensus.io/) - Set of libraries for various languages that allow you to collect application metrics and distributed traces, then transfer the data to a backend of your choice in real time.
* [Opentracing](https://opentracing.io/) - Vendor-neutral APIs and instrumentation for distributed tracing.
* [Openmetrics](https://openmetrics.io/) - An effort to create an open standard for transmitting metrics at scale, with support for both text representation and Protocol Buffers.
* [Micrometer](https://micrometer.io/) - Simple facade over the instrumentation clients for the most popular monitoring systems, allowing you to instrument your JVM-based application code without vendor lock-in. Think SLF4J, but for metrics.

<!--lint ignore double-link-->

* [Elastic Beats](https://github.com/elastic/beats) ⭐ 12,642 | 🐛 1,038 | 🌐 Go | 📅 2026-09-03 - Lightweight shippers for Elasticsearch & Logstash, Elastic stack.
* [Tcollector](https://github.com/OpenTSDB/tcollector) ⭐ 509 | 🐛 25 | 🌐 Python | 📅 2024-06-10 - Data collection framework for OpenTSDB.
* [Collectd](http://collectd.org/) - The system statistics collection daemon.
* [Performance Co-Pilot](https://pcp.io/) - System performance analysis toolkit.

<!--lint ignore double-link-->

* [Kube State Metrics](https://github.com/kubernetes/kube-state-metrics) ⭐ 6,193 | 🐛 110 | 🌐 Go | 📅 2026-08-31 - The kube-state-metrics is a simple service that listens to the Kubernetes API server and generates metrics about the state of the objects.
* [Express State Metrics](https://github.com/RafalWilinski/express-status-monitor) ⭐ 3,615 | 🐛 68 | 🌐 JavaScript | 📅 2026-02-16 - Simple, self-hosted module based on Socket.io and Chart.js to report realtime server metrics for Express-based node servers.
* [Netflix Vector](https://github.com/Netflix/vector) ⚠️ Archived - An on-host performance monitoring framework which exposes hand picked high resolution metrics to every engineer's browser.
* [MyPerf4J](https://github.com/LinShunKang/MyPerf4J) ⭐ 3,563 | 🐛 5 | 🌐 Java | 📅 2026-07-31 - High performance Java APM. Powered by ASM. Try it. Test it. If you feel its better, use it.
* [netwatch](https://github.com/matthart1983/netwatch) ⭐ 2,736 | 🐛 1 | 🌐 Rust | 📅 2026-08-31 - Network diagnostics TUI for operators: real-time per-process connection attribution via an eBPF kprobe (with `lsof`/`ss` fallback), libpcap-based deep packet inspection across 13 protocols (TLS, QUIC, HTTP, DNS, SSH, MQTT, SNMP, ...), full RFC 9001 QUIC Initial decryption with cross-packet ClientHello reassembly, JA4 fingerprinting, TCP retransmit and out-of-order analytics, and an optional Landlock sandbox. Rust, MIT, macOS and Linux.
* [SkyAPM-dotnet](https://github.com/SkyAPM/SkyAPM-dotnet) ⭐ 1,659 | 🐛 3 | 🌐 C# | 📅 2026-08-01 - Native support agent in C# and .NETStandard platform, with the helps from Apache SkyWalking committer team.
* [pktvisor](https://github.com/ns1labs/pktvisor) ⭐ 523 | 🐛 2 | 🌐 C++ | 📅 2026-08-26 - Observability agent for summarizing high volume, information dense data streams down to lightweight, immediately actionable observability data directly at the edge.
* [inspectIT Ocelot](https://github.com/inspectIT/inspectit-ocelot) ⭐ 221 | 🐛 80 | 🌐 Java | 📅 2026-02-11 - Java agent for collecting performance, tracing and business data.
* [duplicacy-exporter](https://github.com/GeiserX/duplicacy-exporter) ⭐ 6 | 🐛 0 | 🌐 Python | 📅 2026-08-01 - Real-time Prometheus exporter for Duplicacy backups with live speed, progress, and completion metrics.
* [Kamon](https://kamon.io/) - Monitoring applications running on the JVM.

### Tracing

* [Sleuth](https://docs.spring.io/spring-cloud-sleuth/docs/current/reference/html/) - Spring Cloud Sleuth implements a distributed tracing solution for Spring Cloud, borrowing heavily from Dapper, Zipkin and HTrace.

<!--lint ignore double-link-->

* [inspectIT Ocelot](https://github.com/inspectIT/inspectit-ocelot) ⭐ 221 | 🐛 80 | 🌐 Java | 📅 2026-02-11 - Java agent for collecting performance, tracing and business data.

### Logging

<!--lint ignore double-link-->

* [Elastic Beats](https://github.com/elastic/beats) ⭐ 12,642 | 🐛 1,038 | 🌐 Go | 📅 2026-09-03 - Lightweight shippers for Elasticsearch & Logstash, Elastic stack.
* [Grafana Alloy](https://github.com/grafana/alloy) ⭐ 3,500 | 🐛 1,217 | 🌐 Go | 📅 2026-09-02 - Grafana's OpenTelemetry Collector distribution that unifies logs, metrics, and traces in a single agent; the supported successor to Promtail and Grafana Agent.
* [mTAIL](http://ophilipp.free.fr/op_tail.htm) - Windows program that extract internal monitoring data from application logs for collection in a timeseries database.

### Events & Problems

* [kubernetes-event-exporter](https://github.com/opsgenie/kubernetes-event-exporter) ⚠️ Archived - This tool allows exporting the often missed Kubernetes events to various outputs so that they can be used for observability or alerting purposes.
* [KubeEye](https://github.com/kubesphere/kubeeye) ⭐ 850 | 🐛 31 | 🌐 Go | 📅 2025-06-25 - Aims to find various problems on Kubernetes, such as application misconfiguration (using Polaris), cluster components unhealthy and node problems (using Node-Problem-Detector).
* [kspan](https://github.com/weaveworks-experiments/kspan) ⭐ 805 | 🐛 21 | 🌐 Go | 📅 2023-06-24 - Turning Kubernetes Events into spans.

## 4. Load Generators and Synthetic Traffic

* [Locust](https://github.com/locustio/locust) ⭐ 28,121 | 🐛 4 | 🌐 Python | 📅 2026-08-26 - Easy-to-use, distributed, user load testing tool. It is intended for load-testing web sites (or other systems) and figuring out how many concurrent users a system can handle.
* [Vegeta](https://github.com/tsenart/vegeta) ⭐ 25,175 | 🐛 122 | 🌐 Go | 📅 2026-02-16 - HTTP load testing tool built out of a need to drill HTTP services with a constant request rate. It can be used both as a command line utility and a library.
* [GoReplay](https://github.com/buger/goreplay) ⭐ 19,318 | 🐛 341 | 🌐 Go | 📅 2026-01-27 - Open-source tool for capturing and replaying live HTTP traffic into a test environment in order to continuously test your system with real data.
* [ghz](https://github.com/bojand/ghz) ⭐ 3,351 | 🐛 101 | 🌐 Go | 📅 2026-09-01 - Simple gRPC benchmarking and load testing tool inspired by hey and grpcurl.
* [Yandex Tank](https://github.com/yandex/yandex-tank) ⭐ 2,596 | 🐛 84 | 🌐 Python | 📅 2026-09-02 - Yandex.Tank is an extensible open source load testing tool for advanced Linux users which is especially good as a part of an automated load testing suite.
* [Taurus](https://github.com/Blazemeter/taurus) ⭐ 2,112 | 🐛 40 | 🌐 Python | 📅 2026-09-02 - Relies on JMeter, Gatling, Locust.io, Grinder and Selenium WebDriver as its underlying tools. Free and open source under Apache 2.0 License.
* [Bender](https://github.com/pinterest/bender) ⭐ 662 | 🐛 6 | 🌐 Go | 📅 2024-04-19 - Makes it easy to build load testing applications for services using protocols like HTTP, Thrift, Protocol Buffers and many more. Bender provides a library of flexible, powerful primitives that can be combined (with plain Go code) to build load testers customized to any use case and that evolve with your service over time.
* [Pandora](https://github.com/yandex/pandora) ⭐ 456 | 🐛 30 | 🌐 Go | 📅 2026-08-18 - High-performance load generator in Go language. It has built-in HTTP(S) and HTTP/2 support and you can write your own load scenarios in Go, compiling them just before your test.
* [phantom](https://github.com/yandex-load/phantom/tree/master/examples) ⭐ 72 | 🐛 4 | 🌐 C | 📅 2020-02-04 - Evgeniy Mamchits' phantom is a very fast (100 000+ RPS) shooter written in C++ (default).
* [Eventum](https://github.com/eventum-generator/eventum) ⭐ 63 | 🐛 17 | 🌐 Python | 📅 2026-09-03 - Data generation platform for producing synthetic event streams based on templates, scripts or log samples.
* [BFG](https://github.com/yandex-load/bfg) ⭐ 22 | 🐛 0 | 🌐 Python | 📅 2017-11-24 - A modular tool and framework for load generation that supports HTTP/2.
* [Trunks](https://github.com/straightdave/trunks) ⭐ 17 | 🐛 0 | 🌐 Go | 📅 2020-11-21 - Like every son, is derived from the father Vegeta with some enhanced skills.
* [JMeter](https://jmeter.apache.org/) - Java application designed to load test functional behavior and measure performance. It was originally designed for testing Web Applications but has since expanded to other test functions.
* [K6](https://k6.io/) - Developer-centric, free and open-source load testing tool built for making performance testing a productive and enjoyable experience.
* [Gatling](https://gatling.io/) - Load test as code.

## 5. Transport

The transport tools simply serve as transport pipelines for data. This includes messaging systems, proprietary protocols and exchange formats.

* [RocketMQ](https://github.com/apache/incubator-rocketmq) ⭐ 22,580 | 🐛 585 | 🌐 Java | 📅 2026-09-03 - A low latency, reliable, scalable, easy to use message oriented middleware born from alibaba massive messaging business.
* [Aeron](https://github.com/real-logic/Aeron) ⭐ 8,838 | 🐛 26 | 🌐 Java | 📅 2026-09-02 - Efficient reliable UDP unicast, UDP multicast, and IPC message transport.
* [Disque](https://github.com/antirez/disque) ⭐ 8,075 | 🐛 59 | 🌐 C | 📅 2021-03-17 - Distributed message broker.
* [VerneMQ](https://github.com/vernemq/vernemq) ⭐ 3,626 | 🐛 167 | 🌐 Erlang | 📅 2026-09-02 - Open source software, extendable, and enterprise support is available.
* [Mist](https://github.com/nanopack/mist) ⭐ 662 | 🐛 6 | 🌐 Go | 📅 2023-09-27 - A distributed, tag-based pub/sub service.
* [Ascoltatori](https://github.com/mcollina/ascoltatori) ⚠️ Archived - Pub/sub library for Node.
* [Malamute](https://github.com/zeromq/malamute) ⭐ 334 | 🐛 28 | 🌐 C | 📅 2025-06-25 - ZeroMQ enterprise messaging broker.
* [Stanza](https://github.com/observIQ/stanza) ⭐ 189 | 🐛 39 | 🌐 Go | 📅 2025-11-20 - Fast and lightweight log transport and processing agent. It's designed as a modern replacement for Fluentd, Fluent Bit, and Logstash.
* [Apache Kafka](http://kafka.apache.org/) - Publish-subscribe messaging rethought as a distributed commit log.
* [Vector](https://vector.dev/) - Collect, transform, and route all your logs and metrics with one simple tool.
* [Redis](https://redis.io/) - Open source, in-memory data structure store, used as a database, cache and message broker. It supports many different data structures such as stringes, hashes, list, etc.
* [Rsyslog](https://www.rsyslog.com/) - The rocket-fast system for log processing.
* [ØMQ](http://zeromq.org/) - Brokerless intelligent transport layer.
* [ActiveMQ](http://activemq.apache.org/) - Powerful open source messaging and integration patterns server.
* [Apollo](http://activemq.apache.org/apollo/) - Faster, more reliable, easier to maintain messaging broker built from the foundations of the original ActiveMQ.
* [Beanstalk](http://kr.github.io/beanstalkd/) - Simple, fast work queue.
* [Eventuate](http://eventuate.io/) - A platform for developing asynchronous microservices solving the distributed data management problems.
* [Mosca](http://www.mosca.io/) - MQTT broker as a module.
* [Mosquitto](http://mosquitto.org/) - Open source message broker that implements the MQTT protocol.
* [Nanomsg](http://nanomsg.org/) - Socket library that provides several common communication patterns for building distributed systems.
* [NATS](https://nats.io/) - Open source, high-performance, lightweight cloud messaging system.
* [NSQ](http://nsq.io/) - A realtime distributed messaging platform.
* [Pulsar](https://pulsar.apache.org/) - Distributed pub-sub messaging system.
* [Qpid](https://qpid.apache.org/) - Cross-platform messaging components built on AMQP.
* [RabbitMQ](https://www.rabbitmq.com/) - Open source Erlang-based message broker that just works.
* [Zenoh](https://zenoh.io/) - A low overhead, low latency, high throughput open-source protocol that blends traditional pub/sub with geo distributed storage, queries and computations for unifying data in motion, data at rest and computations.

## 6. Collector

Receive data from the agents or instrumentation frameworks. The received data is usually persisted to some kind of storage or piped to another tool.

Depending on the collector type, performance data enhancement and modification is also possible inside of the collector.

In addition, collectors can have other responsibilities. For example, some expose the data access API, configuration points for the agents or user interface for interaction with the stored data.

### Metrics

* [Telegraf](https://github.com/influxdata/telegraf) ⭐ 17,791 | 🐛 419 | 🌐 Go | 📅 2026-09-02 - TICK stack, The plugin-driven server agent for collecting & reporting metrics.

<!--lint ignore double-link-->

* [statsd](https://github.com/statsd/statsd) ⭐ 18,078 | 🐛 90 | 🌐 JavaScript | 📅 2025-05-20 - A network daemon that runs on the Node.js platform and listens for statistics, like counters and timers, sent over UDP or TCP and sends aggregates to one or more pluggable backend services.
* [Prometheus](https://prometheus.io/) - The Prometheus monitoring system and time series database.
* [Grafana Mimir](https://grafana.com/oss/mimir/) - Mimir is an open source, horizontally scalable, highly available, multi-tenant TSDB for long-term storage for Prometheus.

### Logging

<!--lint ignore double-link-->

* [Loki](https://github.com/grafana/loki) ⭐ 28,829 | 🐛 1,738 | 🌐 Go | 📅 2026-09-02 - Horizontally-scalable, highly-available, multi-tenant log aggregation system inspired by Prometheus.
* [logdy](https://github.com/logdyhq/logdy-core) ⭐ 2,285 | 🐛 36 | 🌐 Go | 📅 2025-08-25 - Supercharge terminal logs with web browser UI and low-code. It's like jq, tail, less, grep and awk merged together and available in a clean UI. Self-hosted, single binary.
* [Logbook](https://github.com/zalando/logbook) ⭐ 2,063 | 🐛 34 | 🌐 Java | 📅 2026-09-01 - Extensible Java library to enable complete request and response logging for different client- and server-side technologies.
* [Brubeck](https://github.com/github/brubeck) ⚠️ Archived - Statsd-compatible stats aggregator written in C.
* [PFC-JSONL](https://github.com/ImpossibleForge/pfc-jsonl) ⭐ 6 | 🐛 0 | 📅 2026-06-19 - Specialized JSONL log compressor with block-level timestamp indexing for efficient log storage. \~9% compression ratio with Fluent Bit integration and DuckDB queryable archives.
* [logden](https://github.com/ginkida/logden) ⭐ 4 | 🐛 8 | 🌐 Go | 📅 2026-08-28 - Compact centralized logging gateway that ingests logs over HTTP into a Go stdlib service and stores them in ClickHouse, built to run on a \~1 GB RAM VPS.
* [Graylog](https://www.graylog.org/) - Simply great centralized log management.
* [GoAccess](https://goaccess.io/) - Open source real-time web log analyzer and interactive viewer that runs in a terminal in \*nix systems or through your browser. It provides fast and valuable HTTP statistics for system administrators that require a visual server report on the fly.
* [Last9](https://last9.io/docs/logs/) - Unified Logs Explorer with search, filters, SQL query support, and OpenTelemetry-native ingestion.

### Events

* Nothing for the moment :-P

### Configuration & Linters

* [Augur](https://github.com/starkross/augur) ⭐ 63 | 🐛 5 | 🌐 Open Policy Agent | 📅 2026-09-03 - Static analysis linter for OpenTelemetry Collector configurations. Detects misconfigurations, hardcoded credentials, and missing critical components (memory limiters, batch processors) before deployment. Built on OPA/Rego with customizable policies and CI/CD integration.

## 7. Storage

### Time Series Database

<!--lint ignore double-link-->

* [GreptimeDB](https://github.com/GreptimeTeam/greptimedb) ⭐ 6,590 | 🐛 241 | 🌐 Rust | 📅 2026-09-03 - Open-source, cloud-native observability database with unified SQL and PromQL support for metrics, logs, and traces.
* [Netflix Atlas](https://github.com/Netflix/atlas) ⭐ 3,564 | 🐛 8 | 🌐 Scala | 📅 2026-09-01 - Atlas features in-memory data storage, allowing it to gather and report very large numbers of metrics, very quickly.
* [Metric Tank](https://github.com/grafana/metrictank) ⚠️ Archived - Provides high availability and efficient long-term storage, retrieval, and processing for large-scale environments.
* [LynxDB](https://github.com/lynxbase/lynxdb) ⭐ 283 | 🐛 8 | 🌐 Go | 📅 2026-08-15 - Lightweight columnar log analytics database with a pipe-style query language inspired by SPL.
* [Prometheus](https://prometheus.io/) - The Prometheus monitoring system and time series database.
* [VictoriaMetrics](https://victoriametrics.com/) - Fast, cost-effective and scalable monitoring solution and time series database.
* [InfluxDB](https://influxdata.com) - Open-source time series database developed by InfluxData.
* [OpenTSDB](http://opentsdb.net/) - Distributed, scalable time series database, written in Java.
* [kairosDB](http://kairosdb.github.io/) - Fast Time Series Database on Cassandra.
* [Graphite](https://graphiteapp.org/) - Store numeric time-series data and render graphs of this data on demand.
* [M3DB](https://www.m3db.io/) - Fully open source metrics platform built on M3DB, a distributed timeseries database.
* [TimescaleDB](https://www.timescale.com/) - PostgreSQL for time‑series.
* [QuestDB](https://questdb.com/) - The fastest open source time series database.

### Time Series Cache

* [Trickster](https://github.com/Comcast/trickster) ⭐ 2,088 | 🐛 12 | 🌐 Go | 📅 2026-09-02 - Open Source HTTP Reverse Proxy Cache and Time Series Dashboard Accelerator.

### "Meta Projects" (data storage, multi-tenant, aggregation, high availability, etc)

* [Cortex](https://github.com/cortexproject/cortex) ⭐ 5,860 | 🐛 352 | 🌐 Go | 📅 2026-09-03 - Horizontally scalable, highly available, multi-tenant, long term storage for Prometheus.
* [M3](https://github.com/m3db/m3) ⭐ 4,895 | 🐛 228 | 🌐 Go | 📅 2026-08-17 - Distributed TSDB and Query Engine, Prometheus Sidecar, Metrics Aggregator, and more such as Graphite storage and query engine.
* [Promscale](https://github.com/timescale/promscale) ⚠️ Archived - Unified metric and trace observability backend for Prometheus, Jaeger and OpenTelemetry built on PostgreSQL and TimescaleDB.
* [Observatorium](https://github.com/observatorium/observatorium) ⭐ 226 | 🐛 24 | 🌐 Go | 📅 2025-04-16 - This system will allow you to ingest, store and use common observability signals like metrics, logging and tracing.
* [qryn](https://qryn.metrico.in/) - Polyglot monitoring and observability.
* [Thanos](https://thanos.io/) - Highly available Prometheus setup with long term storage capabilities.
* [Opstrace](https://opstrace.com/) - The Opstrace Distribution is a secure, horizontally-scalable, open source observability platform that you can install in your cloud account.
* [Apache HBase](https://hbase.apache.org/) - The Hadoop database, a distributed, scalable, big data store.

### Tracing

<!--lint ignore double-link-->

* [Zipkin](https://github.com/openzipkin/zipkin) ⭐ 17,455 | 🐛 175 | 🌐 Java | 📅 2026-08-06 - A distributed tracing system.
* [Grafana Tempo](https://github.com/grafana/tempo) ⭐ 5,460 | 🐛 175 | 🌐 Go | 📅 2026-09-02 - Open source, easy-to-use and high-scale distributed tracing backend.
* [Jaeger](https://www.jaegertracing.io/) - Monitor and troubleshoot transactions in complex distributed systems.

<!--lint ignore double-link-->

* [Haystack](https://expediadotcom.github.io/haystack/) - A resilient, scalable tracing and analysis system.

### Search Engine

* [Apache Lucene](https://lucene.apache.org/) - Java library providing powerful indexing and search features.
* [Apache Solr](https://solr.apache.org/) - Solr is the popular, blazing-fast, open source enterprise search platform built on Apache Lucene.
* [Elasticsearch](https://www.elastic.co/es/enterprise-search) - Free and Open, Distributed, RESTful Search Engine.

### Graph Database

* [Neo4j](https://github.com/neo4j/neo4j) ⭐ 17,184 | 🐛 249 | 🌐 Java | 📅 2026-08-24 - Graphs for Everyone.
* [ArangoDB](https://www.arangodb.com/) - Natively store data for graph, document and search needs.

### SQL Database

* [PostgreSQL](https://github.com/postgres/postgres) ⭐ 21,990 | 🐛 0 | 🌐 C | 📅 2026-09-03 - Open source relational database.
* [MySQL](https://www.mysql.com/) - Relational database management system.
* [MariaDB](https://mariadb.org/) - Open source relational database.
* [CockroachDB](https://www.cockroachlabs.com/) - Delivers Distributed SQL, combining the familiarity of relational data with limitless, elastic cloud scale, bulletproof resilience, and more.
* [ClickHouse](https://clickhouse.com/) - Fast open-source OLAP database management system.

### NoSQL Database (The Others :-P)

* [Apache Cassandra](https://cassandra.apache.org/) - Scalability and high availability with linear scalability and proven fault-tolerance on commodity hardware or cloud infrastructure.
* [MongoDB](https://www.mongodb.com/) - Document database with the scalability and flexibility that you want with the querying and indexing that you need.
* [Redis](https://redislabs.com/) - Multi-model NoSQL database server enables search, messaging, streaming, graph, and other capabilities.
* [RethinkDB](https://rethinkdb.com/) - Pushes JSON to your apps in realtime.
* [SQLite](https://www.sqlite.org/index.html) - C-language library that implements a small, fast, self-contained, high-reliability, full-featured, SQL database engine.
* [CouchDB](https://couchdb.apache.org/) - Seamless multi-master sync, that scales from Big Data to Mobile, with an Intuitive HTTP/JSON API and designed for Reliability.

## 8. Visualization

### General & Tools

* [Flame Scope](https://github.com/Netflix/flamescope) ⭐ 3,118 | 🐛 40 | 🌐 Python | 📅 2023-10-06 - FlameScope is a visualization tool for exploring different time ranges as Flame Graphs.
* [ExplorViz](https://github.com/ExplorViz) - Live trace visualization for large software landscapes.
* [Flame Graph](https://www.brendangregg.com/flamegraphs.html) - Visualization of profiled software, allowing the most frequent code-paths to be identified quickly and accurately.

### Dashboarding

* [Kibana](https://github.com/elastic/kibana) ⭐ 21,278 | 🐛 14,648 | 🌐 TypeScript | 📅 2026-09-03 - Elastic stack.
* [Chronograf](https://github.com/influxdata/chronograf) ⭐ 1,568 | 🐛 53 | 🌐 TypeScript | 📅 2026-09-02 - User interface and administrative component of the InfluxDB platform.
* [Skooner](https://github.com/skooner-k8s/skooner) ⭐ 1,444 | 🐛 110 | 🌐 JavaScript | 📅 2024-06-30 - Simple Kubernetes real-time dashboard and management.
* [SLO-Tracker](https://github.com/roshan8/slo-tracker) ⭐ 403 | 🐛 2 | 🌐 TypeScript | 📅 2023-01-30 - A simple but effective way to track SLO's and Error budgets. SLO-tracker can be integrated with few alerting tools via webhook integration to receive SLO voilating incidents.
* [KubeStellar Console](https://github.com/kubestellar/console) ⭐ 131 | 🐛 55 | 🌐 TypeScript | 📅 2026-09-03 - AI-powered multi-cluster Kubernetes dashboard with real-time observability across edge and cloud clusters, CNCF project integrations (Prometheus, Grafana, Istio, Falco, OPA), and 160+ monitoring cards.
* [StatLite](https://github.com/PVRLabs/statlite) ⭐ 129 | 🐛 3 | 🌐 Go | 📅 2026-09-03 - Ultra-light self-hosted metrics dashboard for small Spring Boot deployments. Polls Spring Boot Actuator directly, stores samples in SQLite, and runs as a single Go binary.
* [Grafana](https://grafana.com/oss/grafana/) - The first really good dashboard for displaying metrics.

<!--lint ignore double-link-->

* [Grafterm](https://github.com/slok/grafterm) ⭐ 1,139 | 🐛 11 | 🌐 Go | 📅 2022-06-10 - Visualize metrics dashboards on the terminal, like a simplified and minimalist version of Grafana for terminal.
* [PromViz](https://github.com/nghialv/promviz) ⭐ 955 | 🐛 7 | 🌐 Go | 📅 2024-07-02 - Application that helps you visualize the traffic of your cluster from Prometheus data.
* [Grizzly](https://github.com/grafana/grizzly) ⚠️ Archived - A utility for managing various observability resources with Jsonnet.
* [Prometheus](https://prometheus.io/) - The Prometheus monitoring system and time series database.
* [Uchiwa](https://uchiwa.io/#/) - Simple dashboard for the Sensu monitoring framework, built with Go and AngularJS.

### Tracing

<!--lint ignore double-link-->

* [Zipkin](https://github.com/openzipkin/zipkin) ⭐ 17,455 | 🐛 175 | 🌐 Java | 📅 2026-08-06 - A distributed tracing system.
* [Grafana Tempo](https://github.com/grafana/tempo) ⭐ 5,460 | 🐛 175 | 🌐 Go | 📅 2026-09-02 - Open source, easy-to-use and high-scale distributed tracing backend.
* [Jaeger](https://www.jaegertracing.io/) - Monitor and troubleshoot transactions in complex distributed systems.

<!--lint ignore double-link-->

* [Haystack](https://expediadotcom.github.io/haystack/) - A resilient, scalable tracing and analysis system.
* [Last9](https://last9.io/docs/traces/) - Traces Explorer with filtering, span attributes, waterfall visualizations, and SQL ad-hoc querying; fully OpenTelemetry-native.

### Graph of Nodes

* [Vizceral](https://github.com/netflix/vizceral) ⭐ 4,095 | 🐛 54 | 🌐 JavaScript | 📅 2023-11-28 - Component for displaying traffic data on a WebGL canvas. If a graph of nodes and edges with data about traffic volume is provided, it will render a traffic graph animating the connection volume between nodes.
* [Novatec Service Dependency Graph Panel](https://github.com/NovatecConsulting/novatec-service-dependency-graph-panel) ⭐ 214 | 🐛 51 | 🌐 TypeScript | 📅 2026-02-07 - A Grafana panel for visualizing a Service Dependency Graph.

### Uptime

* [BlueWave Uptime](https://github.com/bluewave-labs/bluewave-uptime) ⭐ 10,783 | 🐛 111 | 🌐 TypeScript | 📅 2026-09-03 - Open-source, self-hosted monitoring tool built with React.js, Node.js, and MongoDB, designed to track server uptime, response times, and incidents in real-time with beautiful visualizations.
* [API Status Check](https://apistatuscheck.com) - Free real-time status monitoring for 285 developer APIs across 29 categories, including AWS, Stripe, GitHub, and OpenAI. Track third-party API availability with alerts and status pages.
* [Monitive](http://monitive.com) - Free for 1 service, checked every 10 minutes with unlimited email & twitter alerts.
* [OutageDeck](https://outagedeck.com) - Third-party cloud and SaaS status monitoring with incident history, dependency stack checks, alerts, and a keyless JSON API.
* [UptimeRobot](https://uptimerobot.com) - Free for 50 monitors, checked every 5 minutes.
* [Uptimeify.io](https://uptimeify.io) - Website and API monitoring with global uptime checks, instant alerts, and hosted status pages.
* [OverOps](https://www.overops.com) - Provides Automated Root Cause (ARC) analysis to reduce the time to identify and fix critical production application errors.
* [Freshping](https://freshping.io) - Free for 50 monitors, checked every 1 minutes. Status pages, monitoring of HTTP (and DNS, ICMP, TCP/UDP), select region of monitoring.
* [FlareWarden](https://flarewarden.com) - Uptime, content, dependency, and SSL monitoring with multi-region verification and status pages. Free plan includes 15 monitors, 5-minute checks, and 90 days of history.
* [Oh Dear](https://ohdear.app) - Uptime, performance, SSL certificate, broken link, and DNS monitoring, with hosted status pages.
* [Drumbeats](https://drumbeats.io) - Cron, heartbeat, and HTTP uptime monitoring for background jobs and services, with duration/hang alerts, concurrent-job correlation, incident management, and hosted status pages. Free for up to 50 monitors, 200K Beats/mo, no credit card. One curl ping instruments a job; no agent or SDK.
* [Hyperping](https://hyperping.com) - Uptime, API, cron, and server monitoring from 18 locations, with on-call scheduling, escalation policies, and hosted status pages.
* [Prismix](https://prismix.dev) - Real-time status monitoring and incident tracking for 75+ AI services (OpenAI, Anthropic, Cursor, Gemini). Free REST API at /api/v1/statuses, email/webhook alerts, 30-day uptime history.
* [sunwatch](https://sunwatch.sunfamily.xyz) - Crypto-paid uptime monitoring for side projects. 3 free monitors; extras are $1/monitor/month via USDC on Base. Webhook alerts on down/up state changes. Open source.

## 9. Processing and Analyze and Act

Tools for rocessing the system data.

* Pipeline tools that receive system data in one format, buffer or generate additional value on the raw data, and usually output or store it in another or the same format
* Usually ingests the data from a multitude of sources and also sends the results to different destinations
* Can setup alerts with a simple click or perform complex anomaly detection based on machine learning algorithms
* Send alerts to popular services like Slack, Email, SMS or PagerDuty
* Create custom triggers to perform any action. Integration with the corporative systems like Jira, CI/CD environment, source code anayze tools, etc.

### Processing

* [Vector](https://github.com/timberio/vector) ⭐ 22,509 | 🐛 2,512 | 🌐 Rust | 📅 2026-09-03 - High-performance observability data router. It makes collecting, transforming, and sending logs, metrics, and events easy. It decouples data collection & routing from your services, giving you control and data ownership, among many other benefits.
* [Logstash](https://www.elastic.co/es/products/logstash) - Open source, server-side data processing pipeline that ingests data from a multitude of sources simultaneously, transforms it, and then sends it to your favorite "stash".
* [Fluentd](https://www.fluentd.org/) - Open source data collector for unified logging layer.

<!--lint ignore double-link-->

* [secure-log2test](https://github.com/golikovichev/secure-log2test) ⭐ 2 | 🐛 0 | 🌐 Python | 📅 2026-08-31 - Python CLI that turns structured Kibana and Elasticsearch log exports into runnable pytest regression suites. Runs fully on-premises with no external API calls; auth headers and secret-looking body fields are redacted before output.
* [Haystack](https://expediadotcom.github.io/haystack/) - A resilient, scalable tracing and analysis system.
* [Kapacitor](https://www.influxdata.com/time-series-platform/kapacitor/) - Real-time streaming data processing engine.

### Alerts

* [Sloth](https://github.com/slok/sloth) ⭐ 2,542 | 🐛 16 | 🌐 Go | 📅 2026-06-19 - Easy and simple Prometheus SLO (service level objectives) generator.

<!--lint ignore double-link-->

* [ElastAlert](https://github.com/Yelp/elastalert) ⭐ 7,988 | 🐛 1,401 | 🌐 Python | 📅 2024-08-07 - Easy & Flexible Alerting With Elasticsearch.
* [Bosun](https://bosun.org/) - Is an open-source, MIT licensed, monitoring and alerting system.
* [Last9](https://last9.io/docs/alert-group/) - Alert Studio for managing alerts with flexible grouping, routing, and correlation, built on top of OpenTelemetry signals.

<!--lint ignore double-link-->

* [Prometheus Alertmanager](https://github.com/prometheus/alertmanager) ⭐ 8,602 | 🐛 427 | 🌐 Go | 📅 2026-09-02 - Prometheus stack, Prometheus Alertmanager, written in go.
* [Kapacitor](https://github.com/influxdata/kapacitor) ⭐ 2,375 | 🐛 834 | 🌐 Go | 📅 2026-09-02 - TICK stack, written in go.
* [Haystack](https://expediadotcom.github.io/haystack/) - A resilient, scalable tracing and analysis system.
* [X-Pack](https://www.elastic.co/cn/products/x-pack) - Elastic stack.

<!--lint ignore double-link-->

* [Seyren](https://github.com/scobal/seyren) ⭐ 861 | 🐛 59 | 🌐 Java | 📅 2022-12-16 - An alerting dashboard for Graphite.
* [NthLayer](https://github.com/rsionnach/nthlayer) ⭐ 17 | 🐛 35 | 🌐 Shell | 📅 2026-07-13 - Reliability requirements as code. Generates Grafana dashboards, Prometheus alerts, SLOs, and PagerDuty configs from service.yaml. Includes deployment gates that block deploys when error budget is exhausted.
* [devalerts](https://github.com/sslinNn/devalerts) ⭐ 0 | 🐛 2 | 🌐 Python | 📅 2026-08-28 - Zero-dependency Python library that sends unhandled exceptions straight to Telegram or Slack, with fingerprint-based dedup and rate-limiting.
* [Bosun](https://bosun.org/) - Time Series Alerting Framework.
* [Moira](https://github.com/moira-alert) - Most powerful alerting system, backed by Graphite.
* [Alerta](https://alerta.io/) - Tool used to consolidate and de-duplicate alerts from multiple sources for quick "at-a-glance" visualisation.
* [Flapjack](http://flapjack.io/) - Monitoring notification routing & event processing system.
* [Cabot](https://cabotapp.com/) - Get alerted when services go down or metrics go crazy.

### Triggers

* [Odin](https://github.com/theycallmemac/odin) ⭐ 483 | 🐛 47 | 🌐 Go | 📅 2023-12-08 - A programmable, observable and distributed job orchestration system.
* [prometheus-am-executor](https://github.com/imgix/prometheus-am-executor) ⚠️ Archived - HTTP server that receives alerts from the Prometheus Alertmanager and executes a given command with alert details set as environment variables.

### Anomalies Detection

* [Chaos Genius](https://github.com/chaos-genius/chaos_genius) ⚠️ Archived - ML powered analytics engine for anomaly/outlier detection and root cause analysis.
* [Anomaly Detection in Prometheus Metrics](https://github.com/AICoE/prometheus-anomaly-detector) ⚠️ Archived - Prototype for a Prometheus Anomaly Detector (PAD) which can be deployed on OpenShift. The PAD is a framework to deploy a metric prediction model to detect anomalies in prometheus metrics.
* [Project Scorpio](https://github.com/AICoE/log-anomaly-detector) ⚠️ Archived - Log Anomaly Detector.
* [observability-mcp](https://github.com/ThoTischner/observability-mcp) ⭐ 6 | 🐛 6 | 🌐 TypeScript | 📅 2026-09-01 - Cross-signal anomaly detection (z-score) over Prometheus metrics and Loki logs, exposed to AI agents through the Model Context Protocol. Pluggable connectors for additional backends, weighted health scoring, Web UI, and an ArtifactHub-listed Helm chart.
* [Banshee](https://github.com/bbotte/banshee-detection_system) ⭐ 2 | 🐛 0 | 🌐 Go | 📅 2016-04-22 - Real-time anomalies(outliers) detection system for periodic metrics.
* [Failure Mode and Effects Analysis (FMEA)](https://asq.org/quality-resources/fmea) - Documents current knowledge and actions about the risks of failures, for use in continuous improvement.
* [Prophet](https://facebook.github.io/prophet/) - Forecasting procedure implemented in R and Python. It is fast and provides completely automated forecasts that can be tuned by hand by data scientists and analysts.
* [Anomaly Detection Toolkit (ADTK)](https://adtk.readthedocs.io/en/stable/) - Python package for unsupervised / rule-based time series anomaly detection.

## 10. LLM & AI Observability

As LLMs and AI agents become core to modern applications, observability for these systems has emerged as a discipline of its own. Unlike traditional APM, LLM observability focuses on **prompt tracing**, **token & cost tracking**, **evaluation & quality metrics**, and **agent workflow debugging**.

### Platforms

* [Langfuse](https://github.com/langfuse/langfuse) ⭐ 34,123 | 🐛 877 | 🌐 TypeScript | 📅 2026-09-03 - Open source LLM engineering platform for observability, metrics, evals, prompt management and datasets. Integrates with OpenTelemetry, LangChain, OpenAI SDK, LiteLLM, and more.
* [Opik](https://github.com/comet-ml/opik) ⭐ 21,756 | 🐛 245 | 🌐 Python | 📅 2026-09-03 - Debug, evaluate, and monitor LLM applications, RAG systems, and agentic workflows with comprehensive tracing, automated evaluations, and production-ready dashboards.
* [Arize Phoenix](https://github.com/Arize-ai/phoenix) ⭐ 11,299 | 🐛 965 | 🌐 Python | 📅 2026-09-03 - Open-source AI observability platform for tracing, evaluation, datasets, experiments, prompt management and playground. Built on OpenTelemetry with Python and TypeScript support.
* [Helicone](https://github.com/Helicone/helicone) ⭐ 6,129 | 🐛 156 | 🌐 TypeScript | 📅 2026-08-31 - Open source LLM observability platform and AI Gateway. One line of code to monitor, evaluate, and experiment across 100+ providers.
* [Agenta](https://github.com/Agenta-AI/agenta) ⭐ 4,676 | 🐛 358 | 🌐 TypeScript | 📅 2026-09-02 - Open-source LLMOps platform for prompt playground, prompt management, LLM evaluation, and observability.
* [Latitude](https://github.com/latitude-dev/latitude-llm) ⭐ 4,615 | 🐛 64 | 🌐 TypeScript | 📅 2026-09-02 - Open-source LLM observability and evaluation platform. Traces, monitors, and evaluates AI agents in production, clusters failures into issues, and generates evals from real-world failures. Built on OpenTelemetry with OpenInference and OpenLLMetry support.
* [Pydantic Logfire](https://github.com/pydantic/logfire) ⭐ 4,450 | 🐛 190 | 🌐 Python | 📅 2026-09-02 - AI observability platform for production LLM and agent systems. Built on OpenTelemetry with first-class Pydantic AI support.
* [Laminar](https://github.com/lmnr-ai/lmnr) ⭐ 3,219 | 🐛 113 | 🌐 TypeScript | 📅 2026-09-01 - Open-source observability and analytics platform purpose-built for AI agents. Built in Rust for performance.
* [OpenLIT](https://github.com/openlit/openlit) ⭐ 2,738 | 🐛 65 | 🌐 TypeScript | 📅 2026-09-03 - OTel-native observability and evals for LLMs and GPUs.
* [Langtrace](https://github.com/Scale3-Labs/langtrace) ⭐ 1,229 | 🐛 2 | 🌐 TypeScript | 📅 2025-11-17 - Open source OpenTelemetry-based observability for LLM applications.
* [Heron](https://github.com/Netis/heron) ⭐ 96 | 🐛 3 | 🌐 Rust | 📅 2026-08-18 - Passive, SDK-free observability for LLM and agent traffic. Reconstructs agent turns and service topology from post-TLS HTTP on the wire — no SDK and no proxy in the request path. Decodes OpenAI/Anthropic/Gemini, folds multi-leg proxy hops, auto-classifies vLLM/SGLang/Ollama backends. Single static binary with embedded console, Apache-2.0.
* [Nika](https://github.com/supernovae-st/nika) ⭐ 64 | 🐛 86 | 🌐 Rust | 📅 2026-09-03 - Workflow engine for AI where observability is built into the runtime: every run emits a typed event stream and a hash-chained, tamper-evident trace (`nika trace verify` · `nika trace show`), with static cost floors before the run and per-task cost rows after. Local-first, single Rust binary, AGPL.
* [SourceryKit](https://github.com/ProvablyAI/sourcerykit) ⭐ 19 | 🐛 16 | 🌐 Python | 📅 2026-09-01 - Observability and governance for AI agent egress. Logs every outbound request and MCP handoff and verifies each against a source of truth with a zero-knowledge proof, blocking anything not on the trusted allow-list. Python SDK (source-available) with a hosted verification backend.
* [Lookspan](https://github.com/JoniMartin27/lookspan) ⭐ 7 | 🐛 3 | 🌐 TypeScript | 📅 2026-09-02 - Local-first observability for AI agents. One command (`npx lookspan`) runs a dashboard with traces, a timeline/waterfall view, cost tracking, replay & LLM-as-judge, and datasets. MCP-native, with OpenAI/Anthropic drop-ins and an OpenTelemetry receiver — all data stays on your machine.
* [Seerlens](https://github.com/eladser/seerlens) ⭐ 4 | 🐛 0 | 🌐 C# | 📅 2026-06-23 - Local-first, .NET-first observability and evals for LLM apps. Live tracing, cost in dollars against a budget, CI-gateable evals, and agent/MCP tool-call scoring. Built on OpenTelemetry with .NET, Python and JS SDKs.
* [ClevAgent](https://clevagent.io) - Runtime monitoring for AI agents — heartbeat watchdog, loop detection, cost tracking, auto-restart.
* [Tuning Engines](https://www.tuningengines.com/) - AI control and observability layer for model, MCP, skill, workflow, policy, approval, state-reference, and outcome traces, with cost analytics and governed OpenAI-compatible routing.
* [Traccia](https://traccia.ai) - Open-source observability and governance platform for AI agents. Integrates with OpenAI Agents SDK, CrewAI, LangChain, Claude Code, and more.
* [Respan](https://www.respan.ai/) - Full-stack AI engineering platform for tracing agent workflows, evals with custom graders, prompt management, and an AI gateway routing 250+ models. Supports OTLP ingestion and framework integrations (OpenAI Agents SDK, Vercel AI, LangGraph, Mastra).
* [Voight](https://voight.xyz) - Real-time LLM observability platform. Drop-in SDK wrappers for OpenAI, Anthropic, Vercel AI SDK + hooks for Claude Code and Cursor capture prompts, tokens, cache reads, tool calls, cost, latency, and errors. OpenTelemetry-compatible via `otel: true` opt-in.
* [telemetry.dev](https://telemetry.dev) - OpenTelemetry-native observability for LLM and agent apps: per-span tokens, cost, latency, and errors from any OTLP exporter.

### Instrumentation & SDKs

* [OpenLLMetry](https://github.com/traceloop/openllmetry) ⭐ 7,413 | 🐛 668 | 🌐 Python | 📅 2026-08-10 - Open-source observability for LLM applications, based on OpenTelemetry.
* [MyScale Telemetry](https://github.com/myscale/myscale-telemetry) ⭐ 55 | 🐛 4 | 🌐 Python | 📅 2025-01-02 - Tool designed to enhance the observability of LLM applications by capturing trace data from LangChain-based applications and storing it in MyScaleDB or ClickHouse.
* [BrowserTrace](https://github.com/aaronlab/browsertrace) ⭐ 4 | 🐛 18 | 🌐 Python | 📅 2026-05-14 - Local-first trace viewer for AI browser-agent failures, capturing screenshots, URLs, actions, model I/O, status, errors, and public-safe HTML exports.

### Cost & Usage Tracking

* [Manifest](https://github.com/mnfst/manifest) ⭐ 7,501 | 🐛 106 | 🌐 TypeScript | 📅 2026-09-02 - Open-source real-time cost observability for AI agents. Tracks tokens, costs, messages, and model usage. Self-hostable, privacy-focused, and OTLP-native.
* [onWatch](https://github.com/onllm-dev/onwatch) ⭐ 725 | 🐛 11 | 🌐 Go | 📅 2026-08-20 - Open-source Go CLI that tracks AI API quota usage across 7 providers. Background daemon with SQLite storage, Material Design 3 web dashboard, and zero telemetry.
* [agenttrace](https://github.com/luoyuctl/agenttrace) ⭐ 127 | 🐛 7 | 🌐 Rust | 📅 2026-08-24 - TUI observability for AI coding agents. Tracks cost, tokens, tool failures, anomalies, health, and CI gates across Claude Code, Codex, Gemini CLI, Aider, and Cursor exports.
* [ax](https://github.com/Necmttn/ax) ⭐ 104 | 🐛 35 | 🌐 TypeScript | 📅 2026-08-26 - Local telemetry for AI coding agents.
* [burn0](https://github.com/burn0-dev/burn0) ⭐ 44 | 🐛 2 | 🌐 TypeScript | 📅 2026-08-06 - Open-source Node.js cost observability with one import. Auto-detects and tracks per-request costs for 50+ services (LLMs, SaaS, databases) via HTTP interception. Sub-millisecond overhead, local-first with optional cloud dashboard.
* [Preflight](https://github.com/newrelic-experimental/preflight) ⭐ 41 | 🐛 78 | 🌐 TypeScript | 📅 2026-09-03 - Local-first observability for AI coding assistants. Captures every tool call (reads, edits, commands, searches), tracks USD cost per session/day/week and per model, scores efficiency, and detects anti-patterns (re-reads, blind edits, stuck loops) on a live local dashboard. Offline by default, Apache-2.0; optional New Relic backend for team rollups and alerting. Works with Claude Code, Cursor, Windsurf, Copilot, Zed, Continue.dev, and Amazon Q.
* [whatbroke](https://github.com/arthi-arumugam-git/whatbroke) ⭐ 20 | 🐛 1 | 🌐 TypeScript | 📅 2026-08-06 - CLI that diffs an AI agent's behavior between two runs: dropped or added tool calls, changed arguments and outputs, cost and latency. Imports OTLP GenAI span exports, Langfuse and LangSmith dumps. npx-installable, MIT.
* [Aether](https://github.com/connectchiragg/aether) ⭐ 9 | 🐛 0 | 🌐 Rust | 📅 2026-07-21 - Local observability TUI for Claude Code and Codex. Tracks context, cost, tokens, duration, tools, compactions, agents, code changes, and per-request input attribution from provider-local session files.
* [grafana-llmops-forge](https://github.com/alebgl77/grafana-llmops-forge) ⭐ 1 | 🐛 0 | 🌐 Python | 📅 2026-09-02 - CLI that generates AI/LLM observability dashboards from an existing Grafana, covering FinOps by provider, agents/RAG, and EU AI Act governance. Zero-dependency.

## 11. GPU Observability

As GPU workloads become central to AI/ML production systems, observability at the GPU level has emerged as a discipline of its own. Unlike traditional APM, GPU observability focuses on **CUDA tracing**, **causal chain analysis** linking host kernel events to GPU latency, and **zero-config eBPF instrumentation** for always-on production use.

* [NVTOP](https://github.com/Syllo/nvtop) ⭐ 10,957 | 🐛 147 | 🌐 C | 📅 2026-05-06 - Task monitor for GPUs and accelerators, similar to htop. Multi-vendor support: NVIDIA, AMD, Intel, Apple, Huawei Ascend, Qualcomm Adreno and more.
* [nvitop](https://github.com/XuehaiPan/nvitop) ⭐ 7,133 | 🐛 19 | 🌐 Python | 📅 2026-07-27 - Interactive NVIDIA GPU process viewer with rich Python API. Ships nvitop-exporter for Prometheus metrics and Grafana dashboards, plus ResourceMetricCollector API for custom monitoring and ML framework callbacks.
* [NVIDIA DCGM Exporter](https://github.com/NVIDIA/dcgm-exporter) ⭐ 1,856 | 🐛 186 | 🌐 Go | 📅 2026-09-02 - Official NVIDIA Prometheus exporter for GPU metrics via DCGM. Kubernetes-native with Helm support, Grafana dashboards, per-process GPU metrics, MIG support, and TLS/auth.
* [nvidia\_gpu\_exporter](https://github.com/utkuozdemir/nvidia_gpu_exporter) ⭐ 1,550 | 🐛 6 | 🌐 Go | 📅 2026-09-02 - Lightweight Prometheus exporter for NVIDIA GPUs using nvidia-smi. No DCGM or C bindings required. Works on Linux and Windows with auto-discovered metric fields and Grafana dashboard.
* [HomeLab Monitor](https://github.com/SikamikanikoBG/homelab-monitor) ⭐ 193 | 🐛 13 | 🌐 Python | 📅 2026-09-02 - Self-hosted dashboard that shows which Docker container is actually holding the GPU - per-container VRAM attribution, not just total utilization. Also covers host vitals, Docker health, systemd services, and multiple machines over SSH. MIT license.
* [piqc](https://github.com/paralleliq/piqc) ⭐ 26 | 🐛 8 | 🌐 Python | 📅 2026-09-02 - Model-aware GPU waste scanner for Kubernetes inference clusters. Detects tier misplacement, idle capacity, OOM risk, and CPU:GPU imbalance, each quantified in dollars. Read-only, deploys as a Kubernetes Job.

## 12. Application Performance Monitoring Solutions (APM)

* [Zabbix](https://github.com/zabbix/zabbix) ⭐ 6,337 | 🐛 108 | 🌐 Go Template | 📅 2026-09-02 - Real-time monitoring of IT components and services, such as networks, servers, VMs, applications and the cloud.
* [DeepFlow](https://github.com/deepflowio/deepflow) ⭐ 4,252 | 🐛 268 | 🌐 Go | 📅 2026-08-31 - Implemented Zero Code data collection with eBPF for metrics, distributed tracing, request logs and function profiling, and is further integrated with SmartEncoding to achieve Full Stack correlation and efficient access to all observability data.
* [Odigos](https://github.com/keyval-dev/odigos) ⭐ 3,675 | 🐛 116 | 🌐 Go | 📅 2026-09-03 - Observability Control Plane.
* [DataBuff](https://github.com/databufflabs/databuff) ⭐ 642 | 🐛 12 | 🌐 Java | 📅 2026-09-02 - Open-source AI-native OpenTelemetry APM with an LLM-powered multi-agent workspace for querying traces, service topology, RED metrics, and alerts in natural language.
* [servicenow - Cloud Observability](https://www.servicenow.com/products/observability.html) - Gain AI-powered insights to detect and quickly respond to changes in cloud-native and monolithic applications.
* [coroot](https://coroot.com/) - Open-source eBPF-based observability tool that turns telemetry data into actionable insights, helping you identify and resolve application issues quickly.
* [robusta](https://home.robusta.dev/) - Unified Kubernetes  monitoring, observability, and operations.
* [Kloudfuse](https://www.kloudfuse.com/) - Single unified observability platform for metrics, events, logs and traces.
* [Aspecto](https://www.aspecto.io/) - Troubleshoot performance bottlenecks and errors within your microservices.
* [Circonus](https://www.circonus.com/) - Unified platform for monitoring and analyzing all of your metrics, infrastructure, and applications.

<!--lint ignore double-link-->

* [SigNoz](https://github.com/SigNoz/signoz) ⭐ 32,002 | 🐛 1,553 | 🌐 TypeScript | 📅 2026-09-03 - Monitor your applications and troubleshoot problems in your deployed applications, an open-source alternative to DataDog, New Relic, etc.
* [Pinpoint](https://github.com/pinpoint-apm/pinpoint) ⭐ 13,862 | 🐛 539 | 🌐 Java | 📅 2026-09-03 - APM (Application Performance Management) tool for large-scale distributed systems written in Java / PHP/PYTHON.
* [Falcon Plus](https://github.com/open-falcon/falcon-plus) ⚠️ Archived - An open-source and enterprise-level monitoring system.
* [Hubble](https://github.com/cilium/hubble) ⭐ 4,321 | 🐛 44 | 🌐 Makefile | 📅 2026-09-03 - Network, Service & Security Observability for Kubernetes.
* [Datav](https://github.com/datav-io/datav) ⭐ 3,966 | 🐛 46 | 🌐 TypeScript | 📅 2025-03-04 - A modern apm solution for enterprise, an open-source alternative to DataDog, New Relic, etc.
* [Scouter](https://github.com/scouter-project/scouter) ⭐ 2,182 | 🐛 20 | 🌐 Java | 📅 2026-03-01 - Open source APM (Application Performance Management) tool.
* [Cloudprober](https://github.com/google/cloudprober) ⚠️ Archived - An active monitoring software to detect failures before your customers do.
* [Soda Sql](https://github.com/sodadata/soda-sql) ⚠️ Archived - Data profiling, testing, and monitoring for SQL accessible data.
* [Epsagon](https://github.com/epsagon) - Application Monitoring Built for Containers and Serverless.
* [Chronosphere](https://chronosphere.io/) - Scalable, reliable, and customizable monitoring solution built for cloud-native applications.
* [Centreon](https://www.centreon.com/) - Business-aware and AIOps-ready IT Monitoring.
* [catchpoint](https://www.catchpoint.com/) - From the edge to the cloud, our proactive observability platform gives you the power to fix problems before your users notice.
* [Blue Matador](https://www.bluematador.com/) - Easiest and fastest way to monitor your cloud environments on the market.
  Just provide your read-only credentials and start getting insights in minutes.
* [Aternity](https://www.aternity.com/application-performance-monitoring/) - Simplified high-definition APM visibility leveraging Real User Monitoring, Synthetic Monitoring, and OpenTelemetry, that is scalable, easy to use and deploy, and unifies insights across end users, applications, networks, and the cloud-native ecosystem.
* [AppOptics](https://www.appoptics.com/) - Continuous monitoring built to scale with your applications for less downtime and lower resource usage.
* [Pixie](https://docs.px.dev/) - Open source observability tool for Kubernetes applications. Pixie uses eBPF to automatically capture telemetry data without the need for manual instrumentation.
* [swagger-stats](https://swaggerstats.io/) - API Telemetry and APM.
* [Last9](https://last9.io/) - OpenTelemetry-native observability platform for APM, metrics, logs, and traces, built to handle high-cardinality telemetry at scale.
* [SkyWalking](https://skywalking.apache.org/) - Application performance monitor tool for distributed systems, especially designed for microservices, cloud native and container-based (Docker, Kubernetes, Mesos) architectures.
* [dynatrace APM](https://www.dynatrace.com/platform/application-performance-monitoring/) - Best-in-class APM from the category leader. Ensure application performance, innovate faster, collaborate efficiently, and deliver more value with dramatically less effort.
* [Elastic APM](https://www.elastic.co/es/apm) - Application performance monitoring system built on the Elastic Stack.
* [DataDog](https://www.datadoghq.com/) - Unified Monitoring For Metrics, Traces, & Logs.
* [Middleware](https://middleware.io/) - Full stack observability solution with real-time monitoring and diagnostics.
* [Honeycomb](https://www.honeycomb.io/) - Give all software engineering teams the observability they need to eliminate toil and delight their users.
* [NewRelic](https://newrelic.com/) - Complete view of your applications and operating environment.
* [AppDynamics](https://www.appdynamics.com/) - Business and application performance monitoring.
* [Instrumental](https://instrumentalapp.com) - Real-time application and server monitoring.
* [Kamon apm](https://kamon.io/apm/) - Point and click to find the endpoints, database queries, and API calls that affect your user's experience.
* [Netdata](https://www.netdata.cloud/) - Troubleshoot slowdowns and anomalies in your infrastructure with thousands of per-second metrics, meaningful visualizations, and insightful health alarms with zero configuration.
* [Stagemonitor](https://www.stagemonitor.org/) - An open source solution to application performance monitoring for java server applications.
* [Checkmk Server](https://checkmk.com/) - Monitor your entire hybrid IT infrastructure.
* [Icinga](https://icinga.com/) - The Icinga stack spans six core strengths that cover all aspects of monitoring.
* [Sentry](https://sentry.io/welcome/) - From error tracking to performance monitoring, developers can see what actually matters, solve quicker, and learn continuously about their applications - from the frontend to the backend.
* [Nagios](https://www.nagios.com/) - Computer system, network and infrastructure monitoring software application.
* [Sensu](https://sensu.io/) - The Observability Pipeline that delivers monitoring as code on any cloud.
* [Kieker](https://kieker-monitoring.net/) - Monitoring, analysis and tool integration.

<!--lint ignore double-link-->

* [rrweb](https://github.com/rrweb-io/rrweb) ⭐ 20,106 | 🐛 427 | 🌐 TypeScript | 📅 2026-08-24 - Open-source session replay library that records the DOM and user interactions as a typed JSON event stream and replays them. Powers the session replay features of Sentry, PostHog, Amplitude, and Highlight.
* [App Health](https://github.com/sass-maker/app-health) ⭐ 0 | 🐛 0 | 🌐 TypeScript | 📅 2026-09-01 - Privacy-first endpoint health for Node, Go, and OpenTelemetry services; projects only method, normalized route, status, duration, timestamp, and optional release into aggregate views.
* [Sematext Cloud](https://sematext.com/) - Infrastructure, log, and digital experience monitoring with service and log auto-discovery. Basic plan is free.
* [TraceKit](https://tracekit.dev) - Lightweight APM combining distributed tracing, live breakpoints, and session replay. Built on OpenTelemetry with SDKs for 13+ languages (frontend to backend).
* [Apitally](https://apitally.io) - API monitoring, analytics, and request logging for REST APIs, with lightweight open-source SDKs for Python, Node.js, Go, .NET, and Java.
* [groundcover](https://www.groundcover.com/) - eBPF-based observability platform for Kubernetes with logs, metrics, traces, and APM; deployed entirely inside the user's own cloud (BYOC) for data residency.
* [CoreDash](https://coredash.app) - Real user monitoring for Core Web Vitals (LCP, INP, CLS, TTFB, FCP) with element level attribution, phase breakdowns, LoAF data, and a built in MCP server for AI agents. EU hosted, GDPR compliant.
* [Muscula](https://muscula.com/) - Error tracking, centralized logging, uptime monitoring, and debugging platform with AI agent integration via Model Context Protocol (MCP) and CLI for modern applications and websites.

## 13. Service Mesh

* [Istio](https://istio.io/latest/docs/concepts/observability/) - Generates detailed telemetry for all service communications within a mesh.
* [Kiali](https://www.kiali.io/) - Observability console for Istio with service mesh configuration capabilities. It helps you to understand the structure of your service mesh by inferring the topology, and also provides the health of your mesh.

## 14. Observability as a Service

* [servicepilot](https://www.servicepilot.com/en/) - Modern monitoring platform.
* [Instana](https://www.ibm.com/es-es/products/instana) - IBM® Instana® Observability is the gold standard of incident prevention with automated full-stack visibility, 1-second granularity and 3 seconds to notify.

<!--lint ignore double-link-->

* [Epsagon](https://github.com/epsagon) - Application Monitoring Built for Containers and Serverless.
* [Mackerel](https://en.mackerel.io/) - A SaaS server monitoring service with an intuitive UI, optimized for the cloud era, that fosters a culture of team-based system monitoring/operation.
* [Grafana Cloud](https://grafana.com/products/cloud/?plcmt=nav-products-cta1\&cta=cloud) - Composable observability platform, integrating metrics, traces and logs with Grafana.
* [NexClipper](https://github.com/NexClipper) - Full stack visibility and intelligence for cloud native applications.
* [Sysdig Prometheus](https://sysdig.com/products/monitor/) - Cloud scale monitoring solution with full Prometheus compatibility.
* [WhaTap](https://whatap.io/en/) - Provides an integrated monitoring service for DevOps that analyzes application performance issue running on Kubernetes in real time.
* [CloudWatch](https://aws.amazon.com/es/cloudwatch/) - Observability of your AWS resources and applications on AWS and on-premises.
* [Nuberio](https://www.nuberio.com/audit) - Free AWS CloudWatch alarm audit for small teams. Hygiene score out of 100, missing and noisy alarms across 18 AWS services (RDS, Lambda, ECS, ALB), with alarm classification and top fixes — read-only scan, no credentials required.
* [Google Cloud Monitoring](https://cloud.google.com/monitoring) - Gain visibility into the performance, availability, and health of your applications and infrastructure.
* [Azure Monitor](https://azure.microsoft.com/en-us/services/monitor/#overview) - Full observability into your applications, infrastructure, and network.
* [Guance](https://www.guance.com) - China local "All in one" observability platform, it can integrate any open source collecting method.
* [Alibaba Cloud Logs Service](https://www.alibabacloud.com/es/product/log-service) - Complete real-time data logging service that has been developed by Alibaba Group.

<!--lint ignore double-link-->

* [Graylog Cloud](https://www.graylog.org/) - Seamless log data collection, faster analysis, and the answers you need when you need them.
* [humio](https://www.humio.com/) - Modern log management with streaming observability and affordable Unlimited Plans.
* [logdna](https://www.logdna.com/) - A comprehensive log solution to control all of your log data.
* [loggly](https://www.loggly.com/) - See it all in one place. Dozens of log sources, no proprietary agents.
* [SCALYR](https://www.scalyr.com/) - Log analytics - blazing fast at petabyte scale, feature rich at surprisingly low cost.
* [splunk](https://www.splunk.com/) - Extensible data platform powers unified security, full-stack observability and limitless custom applications.
* [sumo logic](https://www.sumologic.com/) - Reduce downtime with real-time alerting, dashboards, and machine-learning-powered analytics for all three types of telemetry — logs, metrics, and traces.
* [Tencent Cloud Log Service](https://cloud.tencent.com/product/cls) - Tencent is an internet service portal offering value-added internet, mobile, telecom, and online advertising services.
* [Geneos](https://www.itrsgroup.com/products/geneos) - Real-time monitoring for all your environments in one platform.
* [Levitate](https://last9.io/levitate-tsdb) - A Time Series Data Warehouse and Cloud Native Monitoring Solution.

<!--lint ignore double-link-->

* [Sematext Cloud](https://sematext.com/) - Infrastructure and log monitoring with service and log auto-discovery. Basic plan is free. Website uptime, API, and SSL certificate monitoring. Includes status pages and scriptable multi-page user transaction monitoring, etc.
* [Dash0](https://www.dash0.com/) - Modern OpenTelemetry Native Observability, built on CNCF Open Standards such as PromQL, Perses and OLTP with full cost control. Supports monitoring metrics, logs and traces. With dashboarding and alerting capabilities.
* [Uptrack](https://uptrack.app) - Uptime monitoring with 30-second checks on the free tier, consecutive-check alert confirmation (multi-region majority vote), hosted status pages, and a built-in MCP server for AI-agent-driven incident triage. HTTP, SSL, TCP, DNS, Ping, Heartbeat, and Cron monitors.
* [Rivana](https://rivana.io) - Storage-fleet monitoring for enterprise SSD/HDD fleets, tracking 10,000+ devices across thousands of hosts to surface latency and performance issues that generic monitoring and SMART alerts miss.
* [Yorker](https://yorkermonitoring.com) - OpenTelemetry-native synthetic monitoring. Runs HTTP and Playwright browser checks and forwards each run as enriched OTLP (anomaly scoring, third-party attribution, W3C traceparent) to any OTel backend.

## 15. Examples and Sandboxes

* [Spring PetClinic Sample Application](https://github.com/spring-petclinic/spring-petclinic-microservices) ⭐ 2,193 | 🐛 12 | 🌐 Java | 📅 2026-08-21 - Distributed version of the Spring PetClinic Sample Application built with Spring Cloud.
* [FastAPI with Observability](https://github.com/Blueswen/fastapi-observability) ⭐ 1,115 | 🐛 6 | 🌐 Python | 📅 2026-04-12 - Docker ready. Telemetry FastAPI application with three pillars of observability: Traces (Tempo), Metrics (Prometheus), Logs (Loki) on Grafana through OpenTelemetry and OpenMetrics. Using examplar for cross querying between traces, metrics and logs.
* [Grafana tns](https://github.com/grafana/tns) ⭐ 241 | 🐛 23 | 🌐 Jsonnet | 📅 2026-09-03 - Observability Demo App.
* [My Observability Sandbox](https://github.com/adriannovegil/observability-sandbox) ⭐ 9 | 🐛 0 | 🌐 Shell | 📅 2023-04-03 - Get up and running with Prometheus, Thanos, Grafana, and more using Docker and Docker Compose.
* [OpenChainBench](https://github.com/ChainBench/OpenChainBench) ⭐ 7 | 🐛 11 | 🌐 Go | 📅 2026-09-02 - Open benchmark stack for Blockchain RPC providers. Multi-region harnesses scrape live tx-landing, latency and finality metrics; Next.js front-end exposes the dashboards and the raw Prometheus data ([website](https://openchainbench.com)).
* [Node.js boilerplate app (JavaScript)](https://github.com/Olivr/app-node-js) ⭐ 4 | 🐛 22 | 🌐 JavaScript | 📅 2026-04-15 - Docker and Kubernetes ready. Observability (logs, metrics, traces) included.
* [My Spring PetClinic Sample Application](https://github.com/adriannovegil/spring-petclinic-microservices-sre) ⭐ 2 | 🐛 0 | 🌐 Java | 📅 2022-07-07 - My fork of the official repository.

## 16. References

* <https://github.com/crazy-canux/awesome-monitoring> ⭐ 752 | 🐛 22 | 🌐 Go | 📅 2025-02-25
* <https://github.com/Enapiuz/awesome-monitoring> ⭐ 423 | 🐛 13 | 📅 2026-08-04
* [My Awesome Chaos Engineering Repo ;-)](https://github.com/adriannovegil/awesome-chaos-engineering) ⭐ 45 | 🐛 2 | 📅 2026-07-20
* [My Awesome SRE Repo ;-)](https://github.com/adriannovegil/awesome-sre) ⭐ 13 | 🐛 3 | 📅 2026-07-20
* [My Awesome Profiling Repo ;-)](https://github.com/adriannovegil/awesome-profiling) ⭐ 12 | 🐛 1 | 📅 2026-07-20
* <https://speakerdeck.com/adriancole/observability-3-ways-logging-metrics-and-tracing>
* <https://landscape.cncf.io/>
* <https://www.influxdata.com/products/>

## 17. License

[![CC0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/cc-zero.svg)](https://creativecommons.org/publicdomain/zero/1.0)

## 18. Contributing

Contributions welcome! Read the [contribution guidelines](contributing.md) first.

Thank you!

***

> _Enhansomed by [enhansome](https://github.com/enhansome) on 2026-09-03._
