![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2018-12-26)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
117.156.234.3|-|10
119.97.170.34|34.170.97.119.broad.wh.hb.dynamic.163data.com.cn|9
171.25.193.235|tor-exit3-readme.dfri.se|9
128.199.140.214|exchangercoin.com|9
163.172.132.199|199-132-172-163.rev.cloud.scaleway.com|9
171.25.193.20|tor-exit0-readme.dfri.se|9
80.82.77.139|dojo.census.shodan.io|9
1.237.178.27|-|9
51.15.53.83|83-53-15-51.rev.cloud.scaleway.com|8
122.226.181.165|-|8
122.226.181.164|-|8
185.117.215.9|tor3.digineo.de|8
89.234.157.254|marylou.nos-oignons.net|8
218.48.59.189|-|8
171.25.193.25|tor-exit5-readme.dfri.se|8
197.231.221.211|exit1.ipredator.se|8
65.19.167.131|-|8
65.19.167.132|-|8
5.199.130.127|j061.jade.fastwebserver.de|8
35.0.127.52|tor-exit.eecs.umich.edu|8
80.67.172.162|algrothendieck.nos-oignons.net|8
58.42.228.170|-|8
42.61.24.202|-|8
171.25.193.78|tor-exit4-readme.dfri.se|8
218.148.136.1|-|8
199.87.154.255|tor.les.net|8
216.239.90.19|tor-gateway.vif.com|8
185.254.120.6|-|8
62.102.148.67|-|8
219.135.194.73|73.194.135.219.broad.gz.gd.dynamic.163data.com.cn|8
69.60.21.172|staging.codeandtheory.com|8
115.233.246.46|-|8
62.210.37.82|62-210-37-82.rev.poneytelecom.eu|8
71.6.158.166|ninja.census.shodan.io|8
192.160.102.166|chaucer.relay.coldhak.com|8
185.220.101.15|-|8
192.160.102.170|ogopogo.relay.coldhak.com|8
58.142.30.94|-|8
185.220.101.33|-|8
198.96.155.3|exit.tor.uwaterloo.ca|8
51.15.43.205|tor4thepeople3.torexitnode.net|8
199.19.225.65||8
119.192.239.192|-|8
121.17.18.219|-|8
185.220.102.8|-|8
115.238.245.2|-|8
122.2.223.242|122.2.223.242.static.pldt.net|8
