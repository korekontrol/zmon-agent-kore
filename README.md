# zmon-agent-kore
ZMON autodiscovery agent

# Motivation
Dynamic entity disovery is very interesting feature of [Zalando ZMON](https://zmon.io). Currently Zalando provides two agents: [zmon-aws-agent](https://github.com/zalando-zmon/zmon-aws-agent) and [zmon-agent-core](https://github.com/zalando-zmon/zmon-agent-core). Those are brilliant solutions and work great inside Zalando. However it might become a little complicated to use those agent outside of Zalando organization for various reasons, as they expect some Zalando-internal-conventions to be in place and might crash given you try to run it on your own infrastructure.

# Architectural decisions
 - use as much as possible from current zmon software, don't reinvent if it can be reused
 - use several discovery mechanisms (AWS, Kubernetes)
 - use feature switches to enable/disable discovery of various entity types
 - be resilient, make sure that the agent discovers what's possible and doesn't crash if requirements for some discoveries are not met (ie. if an IAM role is missing for discovering load balancers, don't crash the process and try to discover all remaining entity types)
 - stay as compatible as possible with entity definition structures used by zalando agents (entity names and fields)
