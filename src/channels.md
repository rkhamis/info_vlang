### Channels
Channels are the preferred way to communicate between coroutines. V's channels work basically like
those in Go. You can push objects into a channel on one end and pop objects from the other end.
Channels can be buffered or unbuffered and it is possible to `select` from multiple channels.

further reading:
- [Syntax and Usage](syntax_and_usage)
- [Channel Select](channel_select)
- [Special Channel Features](special_channel_features)
- [Shared Objects](shared_objects)