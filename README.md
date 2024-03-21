![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

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
ipset -q create ipsum hash:ip
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2024-03-21)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
185.191.127.212|-|9
213.109.202.127|-|9
103.251.167.20|-|9
122.224.37.86|-|9
87.98.138.142|ip142.ip-87-98-138.eu|9
185.224.128.34|-|8
80.82.77.33|sky.census.shodan.io|8
71.6.199.23|einstein.census.shodan.io|8
94.102.49.193|cloud.census.shodan.io|8
213.6.203.226|-|8
83.167.143.89|89-143-167-83.reverse.alphalink.fr|8
185.246.188.73|-|8
45.95.147.236|hosted-by.as49870.net|8
179.43.180.106|hostedby.privatelayer.com|8
185.216.70.138|-|8
185.191.126.213|-|8
71.6.135.131|soda.census.shodan.io|8
185.129.62.63|tor02.zencurity.com|8
185.129.62.62|tor01.zencurity.com|8
14.32.241.81|-|8
193.222.96.163|-|8
182.72.142.62|nsg-static-062.142.72.182.airtel.in|7
91.128.181.91|c91-128-181-91.bredband.tele2.se|7
161.35.71.130|-|7
185.220.101.109|tor-exit-109.digitalcourage.de|7
211.253.10.96|-|7
105.28.108.165|-|7
221.226.39.202|-|7
218.92.0.34|-|7
218.92.0.31|-|7
189.7.17.61|bd07113d.virtua.com.br|7
116.55.245.26|-|7
159.203.10.201|-|7
193.32.162.11|mail.subit.cc|7
68.183.150.225|-|7
122.160.65.215|abts-north-static-215.65.160.122.airtelbroadband.in|7
186.67.248.5|-|7
162.142.125.223|scanner-25.ch1.censys-scanner.com|7
162.142.125.224|scanner-25.ch1.censys-scanner.com|7
218.92.0.76|-|7
36.67.197.52|-|7
41.207.248.204|-|7
138.68.9.83|-|7
112.218.186.98|-|7
165.232.166.202|-|7
218.92.0.107|-|7
157.245.218.29|-|7
82.200.65.218|gw-bell-xen.ll-nsk.zsttk.ru|7
121.227.31.13|-|7
167.172.157.140|lti-lms.ntheye.com|7
167.248.133.124|scanner-26.ch1.censys-scanner.com|7
185.220.101.188|tor-exit-188.relayon.org|7
218.92.0.53|-|7
218.92.0.56|-|7
95.156.96.46|-|7
150.230.133.120|-|7
71.6.146.185|pirate.census.shodan.io|7
178.20.55.16|marcuse.nos-oignons.net|7
178.128.161.183|-|7
167.248.133.38|scanner-08.ch1.censys-scanner.com|7
113.161.158.10|static.vnpt.vn|7
190.104.25.210|lpz-190-104-25-00210.tigo.bo|7
103.86.180.10|-|7
175.207.13.22|-|7
185.220.101.172|tor-exit-172.relayon.org|7
134.209.168.219|-|7
167.94.138.52|scanner-07.ch1.censys-scanner.com|7
106.248.39.107|-|7
71.6.165.200|census12.shodan.io|7
189.6.45.130|bd062d82.virtua.com.br|7
85.209.11.227|-|7
61.177.172.179|-|7
66.240.219.146|burger.census.shodan.io|7
122.166.156.246|abts-kk-static-246.156.166.122.airtelbroadband.in|7
36.134.78.151|-|7
167.94.146.56|-|7
157.245.124.106|-|7
93.174.95.106|battery.census.shodan.io|7
36.110.228.254|-|7
27.72.155.116|dynamic-adsl.viettel.vn|7
59.19.94.35|-|7
80.82.77.139|dojo.census.shodan.io|7
61.177.172.136|-|7
159.203.128.174|-|7
114.118.10.141|-|7
167.248.133.52|scanner-09.ch1.censys-scanner.com|7
92.222.171.6|6.ip-92-222-171.eu|7
218.92.0.29|-|7
218.92.0.22|-|7
218.92.0.24|-|7
218.92.0.27|-|7
61.177.172.140|-|7
185.233.100.23|elenagb.nos-oignons.net|7
167.248.133.185|scanner-29.ch1.censys-scanner.com|7
167.248.133.186|scanner-29.ch1.censys-scanner.com|7
167.248.133.188|scanner-29.ch1.censys-scanner.com|7
167.94.138.126|scanner-27.ch1.censys-scanner.com|7
61.177.172.160|-|7
157.245.50.198|-|7
185.56.83.83|onion.xor.sc|7
124.89.116.178|-|7
180.101.88.205|-|7
65.181.73.155|65-181-73-155.static.imsbiz.com|7
66.240.192.138|census8.shodan.io|7
222.168.30.19|-|7
162.142.125.216|scanner-05.ch1.censys-scanner.com|7
134.209.156.5|-|7
221.162.209.158|-|7
220.80.223.144|-|7
80.67.167.81|nosoignons.cust.milkywan.net|7
218.92.0.112|-|7
218.92.0.113|-|7
218.92.0.118|-|7
211.199.187.14|-|7
61.83.103.96|-|7
182.75.197.174|nsg-static-174.197.75.182-airtel.com|7
220.86.29.35|-|7
190.144.14.170|-|7
103.179.165.186|-|7
175.206.107.100|-|7
43.163.210.148|-|7
180.101.88.197|-|7
185.196.8.151|-|7
167.94.145.58|-|7
221.156.105.215|-|7
211.62.68.204|-|7
218.156.108.222|-|7
180.101.88.196|-|7
151.177.201.230|c151-177-201-230.bredband.tele2.se|7
167.248.133.125|scanner-26.ch1.censys-scanner.com|7
167.248.133.122|scanner-26.ch1.censys-scanner.com|7
89.97.218.142|89-97-218-142.ip19.fastwebnet.it|7
59.24.127.242|-|7
118.122.38.37|-|7
202.21.123.196|-|7
185.165.190.34|red.census.shodan.io|7
180.184.135.15|-|7
167.94.145.59|-|7
167.94.145.51|-|7
114.96.71.150|-|7
103.92.24.242|-|7
80.67.172.162|algrothendieck.nos-oignons.net|7
