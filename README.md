# SOCKS 6 Golang implementation

Not production ready.

## Progress

currently based on draft 11

done: finished
n/a: not applicable
todo: will do
how: investigating API design
wtf: want to do, but has technical problem

- Message parse and serialize (done)
- Handshake (#3, done)
    - Initial data (#3, server done, client how)
    - Authenticate (server done, client todo)
    - Authenticate protocol (#3, server done, client todo)
    - Version mismatch (#5, server done, client n/a)
- Commands (#7)
    - NOOP (#7, server done, client how)
    - CONNECT (#7.1, done)
    - BIND (#7.2, server done, client todo)
    - UDP ASSOCIATE (#7.3, todo)
        - Over TCP
        - Over UDP/DTLS
        - Proxy UDP server (#7.3.1, server n/a, client todo)
        - Proxy multicast (#7.3.2, todo)
        - ICMP Error (#7.3.3, todo)
- Options (#8)
    - Stack options (#8.1, server done, client todo)
        - TOS (#8.1.1, wtf)
        - Happy eyeballs (#8.1.2, todo)
        - TTL (#8.1.3, wtf)
        - No fragmentation (#8.1.4, wtf)
        - TFO (#8.1.5, wtf)
        - Multipath (#8.1.6, wtf)
        - Listen backlog (#8.1.7, server done, client how)
        - Port parity (#8.1.9, how)
    - Session (#8.4, todo)
    - Idempotence (#8.5, todo)
- Authentication methods
    - Username password (#9, server done, client todo)

Many stack options require `setsockopt()`, which will (indirectly) cause the connetion can't closed by `net.Conn.Close()`.
Some even needs break TCP model.
A fd based new network stack is needed in order to support them.

## Reference

- [SOCKS 6 draft GitHub repo](https://github.com/45G/socks6-draft)
- [SOCKS 6 draft IETF tracker](https://datatracker.ietf.org/doc/draft-olteanu-intarea-socks-6/)
- [go-shadowsocks2](https://github.com/shadowsocks/go-shadowsocks2)
- [v2ray](https://github.com/v2fly/v2ray-core)
