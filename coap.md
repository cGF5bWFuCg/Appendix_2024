# CoAP
The summary of the outputs of the logs used in the research can be seen in this section.

# aiocoap.log
1. High Volume of Incoming Requests
```bash
DEBUG:coap-server [2023-12-07T12:00:00Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ab, MsgID: 4210)
DEBUG:coap-server [2023-12-07T12:00:01Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ac, MsgID: 4211)
DEBUG:coap-server [2023-12-07T12:00:02Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ad, MsgID: 4212)
DEBUG:coap-server [2023-12-07T12:00:03Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01ae, MsgID: 4213)
DEBUG:coap-server [2023-12-07T12:00:04Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01af, MsgID: 4214)
DEBUG:coap-server [2023-12-07T12:00:05Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01b0, MsgID: 4215)
DEBUG:coap-server [2023-12-07T12:00:06Z] [192.168.198.11] - CoAP request: [GET] /api/test01 (Token: 0x01b1, MsgID: 4216)
```
2. Response Size and Frequency
```bash
DEBUG:coap-server [192.168.191.12] - CoAP response: 2.05 Content (Token: 0x12345, Payload Size: 1024 bytes) Block1: (szx=6/1024, m=1)
```
3. 
```bash
WARN:coap-server [192.168.191.12] - CoAP response: 5.03 Service Unavailable (Token: 0x12345)
```
4. 
```bash
INFO:coap-server [192.168.198.11] - CoAP request: [GET] /test01 (Token: 0x67890)
```
5. 
```bash
ERROR:coap-server - System resource warning: CPU usage at 90%, Memory usage at 80%
```