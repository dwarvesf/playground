---
tags:
  - engineering
  - engineering/backend
auth: Phat Nguyen
github_id: fuatto
date: 2023-09-13
icy: 10
---
## Before the removal

Kafka has been using [Zookeeper](https://cwiki.apache.org/confluence/display/ZOOKEEPER/ProjectDescription) for:
- Keeping track of which brokers are part of Kafka cluster
- Electing the leader of a given partition
- Storing configurations for topics/permissions and current offsets of each consumer group
- Sending health-check notifications to Kafka (new topics, broker comes up/ dies, delete topics...)

## Why 

- Kafka Controller **state** (**metadata**) often doesn't match the Zookeeper state
- Simpler deployment and configuration (as Zookeeper is a separate Java service) e.g: have to set up SASL on both Kafka and Zookeeper to unify the security config model
- Performance issue when a broker joins/leaves a cluster, Zookeeper can be overloaded by a high number of leader election
- Scaling Kafka only supports limitedly up to 200k partitions

## Architecture

![[kafka_architecture.png]]

#### In old architecture

The controller loads its state from Zookeeper quorum (nodes) after election, then pushes the updates (**LeaderAndIsr** and **UpdateMetadata** messages) to other nodes. 

#### In **KRaft Mode**

The Zookeeper quorum is replaced by the Controller quorum (which manages all metadata that is stored in Zookeeper, e.g: topics, partitions, ISRs, configs...).

An active controller, aka the leader controller, is elected by using [Raft](https://raft.github.io/) (a consensus algorithm) without relying on any external system, handles any RPCs call from the brokers. The follower controllers replicate the data which is written to the active controller to be ready whenever the active controller fails.

The brokers will fetch updates from the active controller via the new **MetadataFetch** API - the broker will track the offset of the last updates it fetched and only request newer updates.

With this KRaft Mode, the controller quorum does not need to load state from Zookeeper when the leadership changes, therefore drastically improving the performance:

![[time-shutdown-operations-kafka.png]]

For simple local setup, can refer at [apache kafka](https://kafka.apache.org/quickstart) , for detailed configurations, can refer at [kraft config](https://kafka.apache.org/documentation/#kraft_config) 

## References
- [https://www.conduktor.io/kafka/zookeeper-with-kafka/](https://www.conduktor.io/kafka/zookeeper-with-kafka/ "https://www.conduktor.io/kafka/zookeeper-with-kafka/")
- [https://developer.confluent.io/learn/kraft/](https://developer.confluent.io/learn/kraft/ "https://developer.confluent.io/learn/kraft/")
- [https://raft.github.io/](https://raft.github.io/ "https://raft.github.io/")
- [https://cwiki.apache.org/confluence/display/KAFKA/KIP-500%3A+Replace+ZooKeeper+with+a+Self-Managed+Metadata+Quorum](https://cwiki.apache.org/confluence/display/KAFKA/KIP-500%3A+Replace+ZooKeeper+with+a+Self-Managed+Metadata+Quorum "https://cwiki.apache.org/confluence/display/KAFKA/KIP-500%3A+Replace+ZooKeeper+with+a+Self-Managed+Metadata+Quorum")
- [https://kafka.apache.org/documentation/#zk](https://kafka.apache.org/documentation/#zk "https://kafka.apache.org/documentation/#zk")