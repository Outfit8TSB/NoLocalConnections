# NoLocalConnections
An example ViaProxy plugin denying connections to local servers.\
This plugin is only needed if you want to host a public SRV mode proxy instance.

## SRV ViaProxy
### Running ViaProxy in SRV mode
To use the SRV mode in ViaProxy you have to change some config options.
```yaml
bind-address: 0.0.0.0:25568 # will translate to viaproxy.0-0-0-0.nip.io:25568
target-address: 127.0.0.1 # unused in srv mode
target-version: 1.8.x # unused in srv mode
auth-method: OpenAuthMod or NONE
wildcard-domain-handling: PUBLIC
```
You have to replace `0.0.0.0:25568` with the address and port you want ViaProxy to run on.\
The `auth-method: openauthmod` is optional and enables [OpenAuthMod](https://github.com/RaphiMC/OpenAuthMod) authentication. Check the caution below.\
The `target-address` and `target-version` are required for ViaProxy to start but don't do anything in SRV mode.
The `auth-method: NONE` is required to use [BungeeViaProxy](https://github.com/ViaVersionAddons/BungeeViaProxy)\

> <b>[CAUTION]</b>\
> `auth-method: openauthmod` will not work unless you installed ViaProxyOpenAuthMod!

### Connecting to ViaProxy in SRV mode
To connect to ViaProxy in SRV mode you need a domain pointing to the IP of the server running ViaProxy.\
The subdomain `viaproxy.` is required for it to work.\
For local connections you can use `viaproxy.127-0-0-1.nip.io`.

To connect to a server through ViaProxy you have to prepend the `server ip`, `server port` and `version` to your domain:
```
address_port_version.viaproxy.hostname(old Format)
address.<address>.port.<port>.version.<version>.f2.viaproxy.hostname(new format)
```

For example to connect to `lenni0451.net:39999` with the version `C0.30-CPE` you can use:
```
lenni0451.net_39999_c0.30-cpe.viaproxy.127-0-0-1.nip.io(old Format)
address.lenni0451.net.port.39999.version.c0.30-CPE.f2.viaproxy.127-0-0-1.nip.io(new format)
```


