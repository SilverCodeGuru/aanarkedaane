Integration

how apps talk to each other in cloud

directly

decoupled

## SQS
4 days default, max 14 days
decouples application tiers
FIFO


## SNS

publishers publish to a topic
subscribers subscribe to a topic


## kinesis

real time big data streaming
low latecy ingestion from thousands of sources
Data Firehose - load kinesis data streams in S3/redshift

## amazon mq

to ease migration from rabbitmq and other mqs
managed message broker for rabbitmq and apache activemq

