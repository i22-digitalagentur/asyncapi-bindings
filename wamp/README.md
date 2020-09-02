# WAMP Bindings

This document defines how to describe WAMP-specific information on AsyncAPI.

<a name="version"></a>

## Version

Current version is `0.1.0`.


<a name="server"></a>

## Server Binding Object

This object contains information about the server representation in WAMP.

##### Fixed Fields

Field Name | Type | Description
---|:---:|---
<a name="serverBindingObjectTransport"></a>`transport` | string | The transport used. Should be one of `websocket`, `rawsocket`, `longpoll`. Defaults to `websocket`.
<a name="serverBindingObjectSubProtocols"></a>`subProtocols` | string[] | The supported websocket subprotocols as a list. The values must be a combination of `json`, `msgpack`, `jsonBatched` and `msgpackBatched`.
<a name="serverBindingObjectMultiplexSupport"></a>`multiplexSupport` | boolean | Indicates whether the server supports multiplexed connections. Defaults to `false`.
<a name="serverBindingObjectAuthentication"></a>`authentication` | string | The type of authentication to use. Should be one of `cookie`, `certificate`, `wampcra`, `ticket`, `wamp-scram`, `httpHeader`.

This object MUST contain only the properties defined above.

##### Example

```yaml
servers:
  production:
    bindings:
      wamp:
        transport: websocket
        subProtocols:
          - json
          - msgpack
        multiplexSupport: false
        authentication: httpHeader
```

<a name="message"></a>

## Message Binding Object

This object contains information about the message representation in WAMP.

##### Fixed Fields

Field Name | Type | Description
---|:---:|---
<a name="messageBindingObjectRealm"></a>`realm` | string | The realm that this message is being published in.

This object MUST contain only the properties defined above.

```yaml
channels:
  user/signup:
    publish:
      message:
        bindings:
          wamp:
            realm: com.example.realm
```
