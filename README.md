# kafka-standalone
run kafka on your laptop easily using a single docker container


This docker container will run both zookeeper and kafka in a single docker container.  You would never want to do this in production, but it's useful for developers to get it running on their laptops for coding purposes.

It is originally based upon the spotify kafka image, which was intended to be used for the same purpose.  However, their image is based upon a very old version of kafka.  This updates the version of kafka to 2.0.0.

Here is the original kafka image:
https://hub.docker.com/r/spotify/kafka/
https://github.com/spotify/docker-kafka

You can run this container like so...

docker run -p 2181:2181 -p 9092:9092 --env ADVERTISED_HOST=localhost --env ADVERTISED_PORT=9092 mrrick/kafka-standalone

export KAFKA=localhost:9092
kafka-console-producer.sh --broker-list $KAFKA --topic test

export ZOOKEEPER=localhost:2181
kafka-console-consumer.sh --zookeeper $ZOOKEEPER --topic test

or with kafkacat:
export KAFKA=localhost:9092
kafkacat -b $KAFKA -t test -P

kafkacat -b $KAFKA -t test
