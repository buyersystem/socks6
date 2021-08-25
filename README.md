# SOCKS 6 Golang implementation

Not production ready.

## Progress

currently based on draft 11

### What works

? means not tested at all

- TCP relay
- Bind
- UDP
- Noop
- Session
- Happy Eyeball Option (RFC6555 only)
- TLS
- IP DF, TTL, TOS Option ? (remote leg only)
- Bind with backlog ? (backlog is simulated) 
- Client API ? (no bind)
- DTLS ?
- Token ?
- Linux ?
- Port parity Option ?

### TODO list

- Follow golang conventions
- Authentication
- Test coverage
- SOCKS 5 to 6 converter ?
- Client demo ?
- ...

### Not TODO

If somebody implemented these feature, just send patch.

- TFO Option. 
    TFO is not supported in Go stdlib, need special OS API to establish TFO connection, need write a custom dialer to do that.
- MPTCP Option.
    Not supported in Go stdlib and some desktop OS (yet).
- UDP Error Option.
    Non privileged ICMP PacketConn in Go is not supported on some desktop OS (yet).
- Multicast UDP
    I need to read the *TCP/IP Illustrated* first...

## Reference

- [SOCKS 6 draft GitHub repo](https://github.com/45G/socks6-draft)
- [SOCKS 6 draft IETF tracker](https://datatracker.ietf.org/doc/draft-olteanu-intarea-socks-6/)
- [go-shadowsocks2](https://github.com/shadowsocks/go-shadowsocks2)