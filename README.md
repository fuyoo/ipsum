![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (every 24 hours) basis and the final result is pushed to this repository. The feed contains IP addresses plus an occurrence count (how many source lists each IP appears on). Higher counts generally mean higher confidence and fewer false positives when blocking inbound traffic. Also, list is sorted by occurrence count (highest to lowest).

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl -fsSL https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "^#" | grep -Ev '[[:space:]]([12])$' | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo -i
apt-get update && apt-get install -y iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:ip
for ip in $(curl https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -Ev '[[:space:]]([12])$' | cut -f 1); do ipset add ipsum $ip; done
iptables -D INPUT -m set --match-set ipsum src -j DROP 2>/dev/null
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2026-03-25)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
2.57.121.112|dns112.personaliseplus.com|10
185.91.69.217|-|10
45.148.10.121|-|9
91.224.92.50|imize2.writeresaychooseboltsnow.com|9
93.174.95.106|battery.census.shodan.io|9
114.111.54.188|-|9
2.57.121.50|smtp50.kcmoa.com|8
2.57.121.86|mta86.soniideas.com|8
14.63.217.28|-|8
43.252.231.122|-|8
61.245.11.87|-|8
66.240.192.138|census8.shodan.io|8
77.239.108.0|-|8
80.82.77.33|sky.census.shodan.io|8
80.82.77.139|dojo.census.shodan.io|8
82.165.66.87|ip82-165-66-87.pbiaas.com|8
86.54.31.34|wine.census.shodan.io|8
86.54.31.42|green.census.shodan.io|8
91.208.206.75|system-patch-node.net|8
152.32.162.42|-|8
167.94.146.57|57.146.94.167.censys-scanner.com|8
167.94.146.60|60.146.94.167.censys-scanner.com|8
168.144.40.190|-|8
196.188.93.169|-|8
217.154.69.208|-|8
2.57.121.17|hosting17.tronicsat.com|7
2.57.121.25|hosting25.tronicsat.com|7
2.57.121.69|mta69.soniideas.com|7
2.57.121.118|dns118.personaliseplus.com|7
2.57.122.189|-|7
2.57.122.195|-|7
2.57.122.197|-|7
2.57.122.238|-|7
5.182.83.231|undefined.hostname.localhost|7
14.63.196.175|-|7
14.116.156.100|-|7
18.218.118.203|scan.visionheight.com|7
27.79.4.8|localhost|7
27.79.7.233|localhost|7
27.111.32.174|-|7
34.85.163.94|94.163.85.34.bc.googleusercontent.com|7
34.175.118.185|185.118.175.34.bc.googleusercontent.com|7
35.237.94.18|18.94.237.35.bc.googleusercontent.com|7
36.255.3.203|-|7
38.250.116.128|-|7
43.128.81.242|-|7
45.15.224.178|-|7
45.43.37.254|-|7
45.87.249.155|-|7
45.148.10.141|-|7
45.148.10.151|-|7
45.148.10.157|-|7
45.148.10.192|-|7
45.175.37.18|-|7
45.227.254.170|-|7
49.64.169.153|-|7
51.158.120.121|121-120-158-51.instances.scw.cloud|7
59.12.160.91|-|7
60.199.224.2|60-199-224-2.static.tfn.net.tw|7
60.244.155.70|-|7
62.193.106.227|-|7
66.132.172.33|33.172.132.66.censys-scanner.com|7
66.132.172.46|46.172.132.66.censys-scanner.com|7
66.132.172.132|132.172.132.66.censys-scanner.com|7
66.132.172.135|135.172.132.66.censys-scanner.com|7
66.132.172.136|136.172.132.66.censys-scanner.com|7
66.132.172.143|143.172.132.66.censys-scanner.com|7
66.132.172.181|181.172.132.66.censys-scanner.com|7
66.132.172.192|192.172.132.66.censys-scanner.com|7
68.233.116.124|-|7
69.5.189.81|VPS-RvrwwwsW|7
71.6.135.131|soda.census.shodan.io|7
71.6.158.166|ninja.census.shodan.io|7
71.6.165.200|census12.shodan.io|7
71.6.199.23|einstein.census.shodan.io|7
80.66.66.70|-|7
80.94.92.168|-|7
80.94.92.171|-|7
80.94.92.182|-|7
80.94.92.184|-|7
80.253.31.232|-|7
81.183.192.244|51B7C0F4.dsl.pool.telekom.hu|7
82.24.64.32|-|7
86.54.31.32|hat.census.shodan.io|7
86.54.31.40|blue.census.shodan.io|7
87.106.91.226|-|7
88.142.46.185|185.46.142.88.rev.sfr.net|7
89.167.43.70|static.70.43.167.89.clients.your-server.de|7
89.188.72.128|vps1146.basicserver.io|7
89.248.167.131|mason.census.shodan.io|7
92.27.157.252|host-92-27-157-252.static.as13285.net|7
92.118.39.72|-|7
92.118.39.76|-|7
92.118.39.95|-|7
92.154.95.236|lstlambert-656-1-48-236.w92-154.abo.wanadoo.fr|7
94.102.49.193|cloud.census.shodan.io|7
95.58.255.251|95.58.255.251.static.telecom.kz|7
95.167.225.76|-|7
101.47.158.137|-|7
101.126.88.251|-|7
103.49.238.104|ip103-49-238-104.cloudhost.web.id|7
103.63.25.171|ip103-63-25-171.cloudhost.web.id|7
103.81.170.109|-|7
103.144.28.85|-|7
103.148.100.146|-|7
103.154.62.14|-|7
103.182.132.154|-|7
111.119.220.50|ecs-111-119-220-50.compute.hwclouds-dns.com|7
113.164.66.10|static.vnpt.vn|7
115.140.161.61|-|7
116.34.14.135|-|7
118.26.38.251|-|7
121.165.84.80|-|7
122.168.194.41|abts-mp-static-041.194.168.122.airtelbroadband.in|7
125.20.210.182|-|7
125.21.59.218|-|7
134.65.30.157|-|7
138.124.67.78|-|7
139.19.117.130|inet-research-scan-6.mpi-inf.mpg.de|7
144.31.137.41|vm417920.hosted-by.u1host.com|7
147.182.194.60|-|7
154.221.27.234|-|7
161.49.89.39|161.49.89.39.convergeict.com|7
161.132.19.76|sokso.yachay.pe|7
163.7.1.156|-|7
163.7.8.88|-|7
163.7.8.90|-|7
165.154.6.66|-|7
165.154.162.193|-|7
167.94.146.49|49.146.94.167.censys-scanner.com|7
167.94.146.53|53.146.94.167.censys-scanner.com|7
167.94.146.54|54.146.94.167.censys-scanner.com|7
167.94.146.55|55.146.94.167.censys-scanner.com|7
167.94.146.56|56.146.94.167.censys-scanner.com|7
167.94.146.58|58.146.94.167.censys-scanner.com|7
167.94.146.62|62.146.94.167.censys-scanner.com|7
168.138.210.38|-|7
170.238.160.191|-|7
176.120.22.17|-|7
176.126.87.153|vmi1393378.contaboserver.net|7
178.130.46.2|175197.ip-ptr.tech|7
182.18.161.165|static-182-18-161-165.ctrls.in|7
183.82.126.193|183.82.126.193.actcorp.in|7
185.242.3.105|-|7
185.247.184.146|145987.ip-ptr.tech|7
186.96.151.198|fixed-186-96-151-198.totalplay.net|7
188.166.21.201|-|7
193.24.211.93|-|7
193.32.162.145|-|7
193.106.245.20|do-fn.rom.net.pl|7
195.178.110.15|-|7
197.5.145.73|-|7
197.153.57.103|-|7
199.195.248.31|-|7
201.63.223.138|201-63-223-138.customer.tdatabrasil.net.br|7
202.51.214.99|-|7
202.188.47.41|bat-47-41.tm.net.my|7
203.121.40.210|-|7
209.166.46.147|209-166-46-147.client.dsl.net|7
210.66.181.34|h210-66-181-34.static.seed.net.tw|7
210.114.22.126|-|7
213.209.159.158|-|7
213.209.159.159|-|7
218.56.160.82|-|7
218.145.181.48|-|7
219.78.63.235|n219078063235.netvigator.com|7
220.80.223.144|-|7
220.178.8.154|-|7
220.247.223.56|56.sta.idc-2.slt.lk|7
220.247.224.226|-|7
221.161.235.168|-|7
222.107.156.227|-|7
223.197.186.7|223-197-186-7.static.imsbiz.com|7
