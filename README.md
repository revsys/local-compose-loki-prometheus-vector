# Using Loki and Prometheus for Local Development with Docker Compose

## Why?

As developers, we are often asked to include robust logging (hopefully structured)
and metrics for later use in our deployed environment for operations reasons.

However, we don't have great ways to consume them ourselves or even verify
our work.

This git repository gives you a *mostly working* example of how to do this
without a ton of configuration.

## Stack

### Loki

[Loki](https://grafana.com/oss/loki/) is an efficient log aggregation system.
Its role is the equivalent of ElasticSearch in the typical ELK/EFK stacks you
may be familiar with.

### Vector

[Vector](https://vector.dev/) is a logging agent. It collects logs from all of
our containers and sends them to Loki.

It is configured via [docker/vector.yaml](docker/vector.yaml).

### Prometheus

[Prometheus](https://prometheus.io/) is the most popular time series metrics
storage.

It is configured via [docker/prometheus.yml](docker/prometheus.yml).

### Grafana

[Grafana](https://grafana.com/grafana/) is the most popular visualization tool
used by operations teams.

With this set up you can quickly explore the metrics and logs that are being
collected.  You can also create dashboards of information that can be useful
during local development and debugging.

Another reason you may want to create a Dashboard is to verify it's set up
and then export it for use in your deployed environments.

## FAQ

**Q: Doesn't this take up a bunch of resources on my laptop?**

I too was worried about this and was pleasantly surprised how lightweight it
ended up being.  I'm on an M1 Macbook Pro (2021) and it ends up taking up about
200-300 MBs of RAM and 1-2% of CPU.  I would imagine the CPU would be a bit
higher on x86 architectures than arm, but wouldn't imagine it would even
approach 5%.

**Q: What do I need to do to log in my own code?**

All you need to do is have your code emit logging data to stdout, preferably
in a structured format like JSON.  This makes it far easier to search and filter
your log data in meaningful ways.

## Customizing

You can adjust the Vector, Prometheus, and/or Grafana configurations defined
in their respective YAML files and `compose.yml` itself. For example, you
may need to add a [transform](https://vector.dev/guides/level-up/transformation/)
to your Vector configuration to help filter or shape your log data before
sending it on to Loki.
