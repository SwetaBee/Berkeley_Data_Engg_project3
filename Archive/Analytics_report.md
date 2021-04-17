# Analytics Report
---

For this project, we are creating a pipeline for the events data within the game "Do You Like Challenge or Do You Play Safe." This report will explain how to recreate this pipeline and do some basic analysis of the data to confirm that the pipeline has worked correctly.

### About the Game

The game is a straightforward mobile game in which users progress through different levels, gaining coins every minute. The longer a user stays on a level, the more coins they will gain, however, the chance that the base will be destroyed while they are on that level. To level up, a user needs to have a certain number of coins. As the levels progress, the chance of base destruction increases, as does the amount of coins accrued per minute. If a user earns 5000 coins without having their base destroyed, they win the game.

![Visual of game execution flow](/game_flow.png "Game flow")

The analytics team is interested in tracking several events within the game:
- users accruing coins
- users leveling up
- bases being upgraded
- bases being destroyed

### Building the Pipeline

The pipeline for the game event data includes the following containers, which are deployed by Docker Compose (see docker-compose.yml in the directory):

- Zookeeper is the forwarder that must be used in tandem with Kafka. Zookeeper will store the data in the queue for Kafka.
- Kafka is the data broker in the pipeline. Kafka will be used to publish or consume messages from the queue.
- Cloudera is the container that allows the use of Hadoop Distributed File System (HDFS). HDFS will be used to store the data once it has been processed and filtered.
- Spark is the data processer in the pipeline. It will be used to read data frome the queue.
- Presto is a SQL query engine. It will be used to make tables from the data.
- MIDS is the container that serves as the Linux operating system. This container enables the use of bash commands.

In order to set up the pipeline and confirm that all the containers were working correctly, we ran the following commands in the CLI:

**spin up the containers**
`docker-compose up -d`

**check that everything loaded**
`docker-compose ps`

### Generating the Data
*explanation of using Apache bench to generate test data for the pipeline*

### Event Analysis
*some basic analysis of the events* 