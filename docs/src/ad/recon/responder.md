---
authors: ShutdownRepo, sckdev
---

# Responder ⚙️

[Responder](https://github.com/lgandx/Responder) (Python) is a great tool for [LLMNR, NBTNS, MDNS poisoning](../movement/mitm-and-coerced-authentications/llmnr-nbtns-mdns-spoofing.md) and [WPAD spoofing](../movement/mitm-and-coerced-authentications/wpad-spoofing.md) but it can also be used in "analyze" modes.

* BROWSER mode: inspect [Browse Service](http://ubiqx.org/cifs/Browsing.html) messages and map IP addresses with NetBIOS names 
* LANMAN mode: passively map domain controllers, servers and workstations joined to a domain with the Browser protocol (see [this](https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/responder-20-owning-windows-networks-part-3/)).
* LLMNR, NBTNS, MDNS modes: inspect broadcast and multicast name resolution requests

The following command will enable the analyze modes and will give interesting information like

* Domain Controller, SQL servers, workstations
* Fully Qualified Domain Name (FQDN)
* Windows versions in used
* The "enabled" or "disabled" state of protocols like LLMNR, NBTNS, MDNS, LANMAN, BROWSER

```bash
responder --interface "eth0" --analyze
responder -I "eth0" -A
```

[https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/responder-20-owning-windows-networks-part-3/](https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/responder-20-owning-windows-networks-part-3/)

## Tips & tricks

> [!TIP]
> * If you're running Responder on macOS, it might not function fully—it will receive NBT requests but may not proceed further.
> * To fix this, simply check your Mac's IP address on your local network and add the option `--externalip=`
>
> ```bash
> responder --interface "$INTERFACE" --externalip=$YOURLOCALNETWORKIP
> ```



