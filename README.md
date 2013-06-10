# Golem Client

Golem is available under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).

For more information look at the [main repository](https://github.com/trevex/golem), [examples](https://github.com/trevex/golem_examples) or the [wiki and tutorials](https://github.com/trevex/golem/wiki).

## API Documentation

The API is very similar to the server, but uses idiomatic JavaScript, so the main difference is the lower-case for method names.

### Connection

#### Connection(addr, debug)

The constructor takes an `addr` (e.g. `ws://127.0.0.1:8080/ws`) and a boolean defining whether debug informations should be output or not.

#### Connection.on(name, callback)

On sets a callback for an event name. There are several predefined events:
* `close` when the connection is lost
* `open` after a successful connection

#### Connection.emit(name, data)

Prepares the event name and data and sends it.

#### Connection.setProtocol(protocol)

Sets the protocol for the connection. The default protocol is JSON-based. `protocol` is an object providing several functions:
* `unpack` takes the incoming data and returns [event name, interstage product]
* `unmarshal` takes the interstage product and returns the unmarshalled object
* `marshalAndPack` takes the event name and data object and return a string or array buffer depending on how the data should be send
For more information on custom protocols see the [wiki page](https://github.com/trevex/golem/wiki/Custom-protocol-using-BSON) or the example [client](https://github.com/trevex/golem_examples/blob/master/public/example_protocol.html)- and [server](https://github.com/trevex/golem_examples/blob/master/example_protocol.go)-source.

#### Connection.enableBinary()

Sets the socket binary type to array buffers. Necessary for protocols using a binary interchange format.


