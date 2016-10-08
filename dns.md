## OpenDNS

[OpenDNS](https://www.opendns.com/home-internet-security/) (IPv4) nameservers:
* 208.67.222.222
* 208.67.220.220

Full list of OpenDNS nameservers on [Wikipedia](https://en.wikipedia.org/wiki/OpenDNS#Name_Server_IP_Addresses) including:
* All 4 IPv4 ones;
* The [IPv6](https://github.com/falling-sky/source/wiki) [ones](https://www.opendns.com/about/innovations/ipv6/); 
* The filtered IPv4 [ones](https://www.opendns.com/setupguide/?url=familyshield) i.e.:
  * 208.67.222.123
  * 208.67.220.123

## Dynamic IP

Ruan's [application](https://github.com/ruanpienaar/myip_erl/blob/68df4b5b0c4158866db594d694f2a709b6a2900e/apps/myip_erl/src/myip_erl.erl#L70) relies on http://www.trackip.net/ip?json (see also http://www.trackip.net/ip and http://www.trackip.net/).

From [StackExchange](http://unix.stackexchange.com/questions/254328/get-the-external-ip-address-in-shell-without-dig-in-2016):
* Using [host](https://www.freebsd.org/cgi/man.cgi?query=host&manpath=FreeBSD+10.3-RELEASE): `$ host myip.opendns.com resolver1.opendns.com`
* Using [dig](https://www.freebsd.org/cgi/man.cgi?query=dig&manpath=FreeBSD+10.3-RELEASE+and+Ports): `$ dig myip.opendns.com @resolver1.opendns.com`

OpenDNS appears to offer a free [service](https://diagnostic.opendns.com/myip).

## Dynamic DNS

List of dynamic DNS services in [ddclient](https://github.com/wimpunk/ddclient/tree/a9ab60e7a16bd266f61139eb3c38b1a26cee783d#ddclient-v383), that is also official client [for](https://support.opendns.com/hc/en-us/articles/227987707-Where-do-I-download-an-OpenDNS-Dynamic-IP-updater-client-) OpenDNS Dynamic IP service.

### DuckDNS

Reviews in [GNU tomorrow](http://www.gnutomorrow.com/best-free-dynamic-dns-services-in-2013/) and [lifehacker](http://lifehacker.com/duckdns-duckdns-is-a-simple-easy-dynamic-dns-service-t-1561564166).
