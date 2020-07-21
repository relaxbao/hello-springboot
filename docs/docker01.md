# docker search mysql 查看MySQL版本报错解决

### 1.1 docker search mysql 查看MySQL版本, 报错

```bash
➜  mall-learning git:(master) ✗ docker search mysql
Error response from daemon: Get https://index.docker.io/v1/search?q=mysql&n=25: EOF
```

### 1.2 修改hosts

第一步：通过`dig @114.114.114.114 registry-1.docker.io`找到可用IP

```bash
➜  ~ dig @114.114.114.114 registry-1.docker.io

; <<>> DiG 9.8.3-P1 <<>> @114.114.114.114 registry-1.docker.io
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47220
;; flags: qr rd ra; QUERY: 1, ANSWER: 8, AUTHORITY: 4, ADDITIONAL: 9

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;registry-1.docker.io.        IN    A

;; ANSWER SECTION:
registry-1.docker.io.    3600    IN    A    54.164.230.151
registry-1.docker.io.    3600    IN    A    35.169.231.249
registry-1.docker.io.    3600    IN    A    34.205.207.96
registry-1.docker.io.    3600    IN    A    34.200.28.105
registry-1.docker.io.    3600    IN    A    52.204.202.231
registry-1.docker.io.    3600    IN    A    54.152.209.167
registry-1.docker.io.    3600    IN    A    52.22.181.254
registry-1.docker.io.    3600    IN    A    52.54.216.153

...
```

第二步：尝试修改`/etc/hosts`强制`docker.io`相关的域名解析到其它可用IP

```
54.164.230.151 registry-1.docker.io
```

保存后，重试

```bash
➜  mall-learning git:(master) ✗ docker search mysql
NAME                              DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
mysql                             MySQL is a widely used, open-source relation…   9634                [OK]
mariadb                           MariaDB is a community-developed fork of MyS…   3500                [OK]
mysql/mysql-server                Optimized MySQL Server Docker images. Create…   702
```