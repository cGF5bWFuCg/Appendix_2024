# CoAP
The summary of the outputs of the logs used in the research can be seen in this section.

# aiocoap.log
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
# /var/log/syslog
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