---
title: Messages as Interfaces
summary: 'NServiceBus allows supports the use interfaces as well as standard XSD and class serialization.'
component: core
reviewed: 2019-01-10
redirects:
- nservicebus/messages-as-interfaces
---

NServiceBus support using interfaces as messages types.

Using interfaces allows "multiple inheritance" where one message can inherit from varieties of other messages. This is useful for solving certain "message evolution" scenarios.

Imagine that the business logic represents a state machine with states X and Y. When the system gets into state X, it publishes the message `EnteredStateX`. When the system gets into state Y, it publishes the message `EnteredStateY`. (For more information on how to publish a message, see below.)

In the next version of the system, a new state Z is added, which represents the co-existence of both X and Y states. This can be achieved by defining a message `EnteredStateZ` which would inherits both `EnteredStateX` and `EnteredStateY`.

When the system publishes the `EnteredStateZ` event, the clients that are subscribed to either of `EnteredStateX` or `EnteredStateY` are notified.

{{WARNING:

The following serializers **do not support** messages defined as interfaces: 

 * [Bond](/nservicebus/serialization/bond.md)
 * [MessagePack](/nservicebus/serialization/messagepack.md)
 * [MsgPack](/nservicebus/serialization/msgpack.md)
 * [Protobuf-Net](/nservicebus/serialization/protobufnet.md)
 * [Protobuf-Google](/nservicebus/serialization/protobufgoogle.md)
 * [Wire](/nservicebus/serialization/wire.md)
 * [ZeroFormatter](/nservicebus/serialization/zeroformatter.md)
}}

Without the ability to inherit a message from other message types, composition techniques would be required, thereby preventing the infrastructure from automatically routing messages to pre-existing subscribers of the composed messages.