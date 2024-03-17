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

### Vector

### Prometheus

### Grafana

## FAQ

**Q: Doesn't this take up a bunch of resources on my laptop?**

I too was worried about this and was pleasantly surprised how light weight it
ended up being.  I'm on a M1 Macbook Pro (2021) and it ends up taking up about
200-300 MBs of RAM and 1-2% of CPU.  I would imagine the CPU would be a bit
higher on x86 architectures than arm, but wouldn't imagine it would even
approach 5%.
