# CoAP
The summary of the outputs of the logs used in the research can be seen in this section.

# aiocoap.log
1. High Volume of Incoming Requests
´´´bash
DEBUG:coap-server [192.168.198.11] - CoAP request: [GET] /large-resource Observe: 0 (Token: 0x12345)

too many the same log
´´´
2. 
´´´bash
DEBUG:coap-server [192.168.191.12] - CoAP response: 2.05 Content (Token: 0x12345, Payload Size: 1024 bytes) Block1: (szx=6/1024, m=1)
´´´
3. 
´´´bash
WARN:coap-server [192.168.191.12] - CoAP response: 5.03 Service Unavailable (Token: 0x12345)
´´´
4. 
´´´bash
INFO:coap-server [192.168.198.11] - CoAP request: [GET] /large-resource (Token: 0x67890)
´´´
5. 
´´´bash
ERROR:coap-server - System resource warning: CPU usage at 90%, Memory usage at 80%
´´´