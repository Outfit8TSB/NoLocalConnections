# NoLocalConnections
An example ViaProxy plugin denying connections to local servers.\
This plugin is only needed if you want to host a public Wildcard mode proxy instance.

## Public ViaProxy
### Running ViaProxy in Public Wildcard mode
To use the Public Wildcard mode in ViaProxy you have to change some config options.
```yaml
bind-address: 0.0.0.0:25568 # will translate to viaproxy.0-0-0-0.nip.io:25568
target-address: 127.0.0.1 # unused in srv mode
target-version: 1.8.x # unused in srv mode
auth-method: OpenAuthMod
wildcard-domain-handling: PUBLIC
```
You have to replace `0.0.0.0:25568` with the address and port you want ViaProxy to run on.\
The `auth-method: openauthmod` is optional and enables [OpenAuthMod](https://github.com/RaphiMC/OpenAuthMod) authentication. it needs [ViaProxyOpenAuthMod](https://github.com/viaversionaddons/viaproxyopenauthmod).\
The `target-address` and `target-version` are required for ViaProxy to start but don't do anything in SRV mode.

### Connecting to ViaProxy in SRV mode
To connect to ViaProxy in SRV mode you need a domain pointing to the IP of the server running ViaProxy.\
The subdomain `viaproxy.` is required for it to work.\
For local connections you can use `viaproxy.127-0-0-1.nip.io`.

To connect to a server through ViaProxy using SRV syntax you have to prepend the `server ip`, `server port` and `version` to your domain:
```
address_port_version.viaproxy.hostname
```
For URI Syntax
```
address.<address>.port.<port>.version.<version>.f2.viaproxy.hostname
```

For example to connect to `lenni0451.net:39999` with the version `C0.30-CPE`, 
you can use SRV Syntax:
```
lenni0451.net_39999_c0.30-cpe.viaproxy.127-0-0-1.nip.io
```
or URI Syntax:
```
address.lenni0451.net.port.39999.version.c0.30-cpe.f2.viaproxy.127-0-0-1.nip.io
```


If the domain of a server contains an underscore(Probably it doesnt) you currently can't connect to it since ViaProxy uses the underscore as a separator.
