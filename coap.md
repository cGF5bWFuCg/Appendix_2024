# CoAP
The summary of the outputs of the logs used in the research can be seen in this section.

## aiocoap.log
1. High Volume of Incoming Requests & Repeated Access:
```bash
DEBUG:coap-server [2023-12-07T12:00:00Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ab, MsgID: 4210)
DEBUG:coap-server [2023-12-07T12:00:01Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ac, MsgID: 4211)
DEBUG:coap-server [2023-12-07T12:00:02Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ad, MsgID: 4212)
DEBUG:coap-server [2023-12-07T12:00:03Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ae, MsgID: 4213)
DEBUG:coap-server [2023-12-07T12:00:04Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01af, MsgID: 4214)
DEBUG:coap-server [2023-12-07T12:00:05Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01b0, MsgID: 4215)
DEBUG:coap-server [2023-12-07T12:00:06Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01b1, MsgID: 4216)
```
2. Response Size:
```bash
DEBUG:coap-server [2023-12-07T14:00:06Z] [192.168.191.12] - CoAP response: 2.05 Content (Token: 0x12345, Payload Size: 1024 bytes) Block1: (szx=6/1024, m=1)
```
3. Error Codes:
```bash
WARN:coap-server [2023-12-07T12:00:06Z] [192.168.191.12] - CoAP response: 5.03 Service Unavailable (Token: 0x12345)
```
4. System Resource:
```bash
ERROR:coap-server - System resource warning: CPU usage at 90%, Memory usage at 80%
```
## /var/log/syslog
1. High Network Activity:
```bash
Apr 7 14:11:00 coap-server kernel: [WARN] High TCP traffic volume from 192.168.198.11 to 192.168.191.12 on port 5683
```
2. System Resource Alert:
```bash
Apr 7 14:12:00 coap-server kernel: [ERROR] Memory usage at 90%, possible memory leak detected in process aiocoap-server (pid 12345)
```
3. Failures and Restarts:
```bash
Apr 7 14:14:00 coap-server systemd: [NOTICE] aiocoap-server.service restarted due to unexpected shutdown
```
## /var/log/audit.log
1. Network Activity:
```bash
type=SYSCALL msg=audit(1670405600.123:12345): arch=c000003e syscall=42 success=yes exit=0 a0=3 a1=7fffd395a620 a2=10 a3=7fffd395a3f0 items=0 ppid=3126 pid=3130 auid=1000 uid=1000 gid=1000 euid=1000 suid=1000 fsuid=1000 egid=1000 sgid=1000 fsgid=1000 tty=(none) ses=1 comm="aiocoap-server" exe="/usr/bin/python3.8" subj=system_u:system_r:unconfined_service_t:s0 key=(null)
```
2. Authentication Attempt:
```bash
type=USER_AUTH msg=audit(1670405620.456:12346): pid=3130 uid=0 auid=1000 ses=1 subj=system_u:system_r:unconfined_service_t:s0 msg='op=PAM:authentication acct="root" exe="/usr/bin/su" hostname=? addr=192.168.198.11 terminal=pts/0 res=failed'
```
3. Resource Access:
```bash
type=AVC msg=audit(1670405650.789:12347): avc:  denied  { read } for  pid=3131 comm="aiocoap-server" name="sensitive-config.conf" dev="sda1" ino=1234567 scontext=system_u:system_r:unconfined_service_t:s0 tcontext=system_u:object_r:admin_home_t:s0 tclass=file permissive=0
```
## PCAP File
1. Incoming Request:
```bash
13:45:01.123456 IP 192.168.198.11.12345 > 192.168.191.12.5683: UDP, length 15
```
2. Large Response:
```bash
13:40:01.234567 IP 192.168.191.12.5683 > 192.168.198.11.12345: UDP, length 1400
```
3. Frequent Requests:
```bash
13:44:02.345678 IP 192.168.198.11.12346 > 192.168.191.12.5683: UDP, length 15
13:44:03.456789 IP 192.168.198.11.12347 > 192.168.191.12.5683: UDP, length 15
13:44:04.567890 IP 192.168.198.11.12348 > 192.168.191.12.5683: UDP, length 15
```