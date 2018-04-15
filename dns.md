## Cloudflare

[Cloudflare nameservers](https://developers.cloudflare.com/1.1.1.1/setting-up-1.1.1.1/):
* 1.1.1.1
* 1.0.0.1
* 2606:4700:4700::1111
* 2606:4700:4700::1001

## OpenDNS

[OpenDNS](https://www.opendns.com/home-internet-security/) (IPv4) nameservers:
* 208.67.222.222
* 208.67.220.220

Full list of OpenDNS nameservers on [Wikipedia](https://en.wikipedia.org/wiki/OpenDNS#Name_server_IP_addresses) including:
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

OpenDNS appears to offer a free [service](https://diagnostic.opendns.com/myip), whose domain supports both IPv4 and IPv6 so in order to get your IPv4 address you might have to force IPv4-only address resolution in your client e.g. `$ curl -4 https://diagnostic.opendns.com/myip`.

### Sample cron job

```
$ printf '%s * * * * l() { logger -p user.${1:?} -t %s ${2:?}; }; w() { printf "\\%%b" ${1:?} > ${2:?}; }; U=%s; { curl -f -s ${U:?} || { l warning "Failed HTTP GET to ${U:?}"; exit 1; }; } | { { head -n 1 | grep "^[[:digit:]]\{1,3\}\.[[:digit:]]\{1,3\}\.[[:digit:]]\{1,3\}\.[[:digit:]]\{1,3\}$"; } || { l err "Failed HTTP GET result parsing. Info ${Ip:?}"; exit 1; }; } | { SD=${HOME:?}/.cache/%s; S=${SD:?}/dynamicip; Ip=$(cat -); mkdir -p ${SD:?}; if test ! -e ${S:?}; then { l info "Detected initial IP ${Ip:?}" && w ${Ip:?} ${S:?}; }; elif test ${Ip:?} = $(cat ${S:?}); then l debug "IP remained ${Ip:?}"; else { l notice "IP changed to ${Ip:?}" && w ${Ip:?} ${S:?}; }; fi; }\n' "0,5,10,15,20,25,30,35,40,45,50,55" DYNAMICIP https://www.trackip.net/ip lsb-lucafavatella.github.com | crontab
```

### Restricted email delivery

MailGun - ["10,000 emails free every month. No credit card required."](http://www.mailgun.com/).

Sign up. Explore configs e.g. force TLS. [Authorize](https://mailgun.com/app/account/authorized) recipients.

Get API base URL and API key from [domain](https://mailgun.com/app/domains).

Run [example](https://help.mailgun.com/hc/en-us/articles/202464990-How-do-I-start-sending-email-):
```
$ curl -f -s --user 'api:TODOAPIKEY' https://api.mailgun.net/v3/TODODOMAIN/messages -F from='Excited User <excited@samples.mailgun.org>' -F to='TODORECIPIENTEMAILADDRESS' -F subject='Hello' -F text='Testing some Mailgun awesomeness!'
```

## Dynamic DNS

List of dynamic DNS services in [ddclient](https://github.com/wimpunk/ddclient/tree/a9ab60e7a16bd266f61139eb3c38b1a26cee783d#ddclient-v383), that is also official client [for](https://support.opendns.com/hc/en-us/articles/227987727) OpenDNS Dynamic IP service.

### DuckDNS

Reviews in [GNU tomorrow](http://www.gnutomorrow.com/best-free-dynamic-dns-services-in-2013/) and [lifehacker](http://lifehacker.com/duckdns-duckdns-is-a-simple-easy-dynamic-dns-service-t-1561564166).
