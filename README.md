# posts
.NET Microservices: CQRS &amp; Event Sourcing with Kafka

CQRS: separate read write
-data is more often read than altrerd or created
-scale C&Q APIs independently (few lock contentions when performing C&Q in the same model)
-optimised read and write schemas


Event sourcing - DP
-defines and approach to storing all the changes made to an object/entity as a sequence of immutable events to an ES.
-contains a complete auditable log
-the state of the object(aggregate) can be recreated at any timeframe just by replaying the event store
-improves the write operation, since events are simply appended to the ES


KAFKA
OS, streaming platform
