# MQTT
The summary of the outputs of the logs used in the research can be seen in this section.
# mosquitto.log
1. New Connection From Attacker's IP
```bash
1713510949: New connection from 192.168.198.11:60807 on port 1883.
1713510949: New client connected from 192.168.198.11:60807 as Client_0 (p2, c1, k60).
```
2. Excessive Connection Attempts
```bash
1713510949: New connection from 192.168.198.11:60807 on port 1883.
1713510949: New client connected from 192.168.198.11:60807 as Client_0 (p2, c1, k60).
1713510949: Client Client_0 disconnected.
1713510949: New connection from 192.168.198.11:56391 on port 1883.
1713510949: New client connected from 192.168.198.11:56391 as Client_1 (p2, c1, k60).
1713510949: Client Client_1 disconnected.
1713510949: New connection from 192.168.198.11:47365 on port 1883.
1713510949: New client connected from 192.168.198.11:47365 as Client_2 (p2, c1, k60).
1713510949: Client Client_2 disconnected.
1713510949: New connection from 192.168.198.11:53179 on port 1883.
1713510949: New client connected from 192.168.198.11:53179 as Client_3 (p2, c1, k60).
1713510949: Client Client_3 disconnected.
1713510949: New connection from 192.168.198.11:60291 on port 1883.
1713510949: New client connected from 192.168.198.11:60291 as Client_4 (p2, c1, k60).
1713510949: Client Client_4 disconnected.

```
3. Connections Not Completing MQTT Handshake
```bash
    1614556770: Client attacker_client_001 has exceeded timeout, disconnecting.
```
4. Unusually Long Connection Durations
```bash
    1614556872: Client attacker_client_004 has exceeded timeout, disconnecting.
```
5. Repeated Disconnections and Reconnections
```bash
    1614556882: Client attacker_client_002 disconnected.
    1614556883: New connection from 192.168.198.11 on port 1883. [Client ID: attacker_client_002]
```
6. Error Messages Related to Resource Exhaustion
```bash

    1614556900: Error: Too many connections.
```
```bash
    1623096018: New connection from 192.168.198.11 on port 1883.
    1623096019: New client connected from 192.168.198.11 as attackerClient01 (p2, c1, k60).
    1623096020: Client attackerClient01 sending PUBLISH (d0, q0, r0, m1, 'test/topic', ... (50 bytes)).
    1623096021: New connection from 192.168.198.11 on port 1883.
    1623096021: New client connected from 192.168.198.11 as attackerClient02 (p2, c1, k60).
    1623096022: Client attackerClient02 sending PUBLISH (d0, q0, r0, m2, 'test/topic', ... (50 bytes)).
    1623096025: Client attackerClient01 has exceeded timeout, disconnecting.
    1623096026: Client attackerClient02 has exceeded timeout, disconnecting.
    1623096030: Warning: High CPU usage detected from client connections.
    1623096035: Warning: Memory usage is approaching the limit.
    1623096040: Security Alert: Suspicious activity detected from IP 192.168.198.11. High volume of connections and data packets.
```
# /var/log/syslog
1. Increased System Resource Utilization
```bash
Mar 10 12:34:56 mqtt-server kernel: [12345.678901] Out of memory: Kill process 12345 (mosquitto) score 50 or sacrifice child
Mar 10 12:34:56 mqtt-server kernel: [12345.678902] Killed process 12345 (mosquitto) total-vm:123456kB, anon-rss:12345kB, file-rss:0kB, shmem-rss:0kB
```
2. Network Congestion or Anomalies
```bash
Mar 10 12:35:00 mqtt-server kernel: [123456.789012] TCP: request_sock_TCP: Possible SYN flooding on port 1883. Sending cookies.
```
3. Messages Related to Service Status Changes
```bash
Mar 10 12:40:00 mqtt-server systemd[1]: mosquitto.service: Main process exited, code=killed, status=9/KILL
Mar 10 12:40:01 mqtt-server systemd[1]: mosquitto.service: Failed with result 'signal'.
Mar 10 12:40:05 mqtt-server systemd[1]: mosquitto.service: Service RestartSec=5s expired, scheduling restart.
Mar 10 12:40:05 mqtt-server systemd[1]: mosquitto.service: Scheduled restart job, restart counter is at 1.
Mar 10 12:40:05 mqtt-server systemd[1]: Stopped Mosquitto MQTT v3.1/v3.1.1 Broker.
Mar 10 12:40:05 mqtt-server systemd[1]: Started Mosquitto MQTT v3.1/v3.1.1 Broker.
```

# audit.log
1. Excessive SYSCALL Entries for New Connections
```bash
type=SYSCALL msg=audit(1614556762.123:12345): arch=c000003e syscall=42 success=yes exit=0 a0=3 a1=7fffd39bf6c0 a2=10 a3=7fffd39bf700 items=0 ppid=1 pid=1234 auid=4294967295 uid=1000 gid=1000 euid=1000 suid=1000 fsuid=1000 egid=1000 sgid=1000 fsgid=1000 tty=(none) ses=4294967295 comm="mosquitto" exe="/usr/sbin/mosquitto" key=(null)
```
2. Repeated Connect/Disconnect Events
```bash
type=SYSCALL msg=audit(1614556763.123:12347): ... syscall=42 ... saddr=0200FFFFC0A8C60BC005 ...
type=SYSCALL msg=audit(1614556764.123:12348): ... syscall=... (disconnect) ... saddr=0200FFFFC0A8C60BC005 ...
```
# Network Traffic
1. Numerous TCP Connection Attempts
```bash
No.     | Time      | Source         | Destination    | Protocol | Length | Info
--------|-----------|----------------|----------------|----------|--------|-------------------------
1       | 0.000000  | 192.168.198.11 | 192.168.191.10 | TCP      | 74     | 5060 → 1883 [SYN] Seq=0
```
2. Successful TCP Handshakes
```bash
No.     | Time      | Source         | Destination    | Protocol | Length | Info
--------|-----------|----------------|----------------|----------|--------|-----------------------------------
...     | ...       | ...            | ...            | ...      | ...    | ...
2       | 0.001000  | 192.168.191.10 | 192.168.198.11 | TCP      | 74     | 1883 → 5060 [SYN, ACK] Seq=0 Ack=1
3       | 0.001500  | 192.168.198.11 | 192.168.191.10 | TCP      | 66     | 5060 → 1883 [ACK] Seq=1 Ack=1
```
3. Keep-Alive Packets
```bash
No.     | Time      | Source         | Destination    | Protocol | Length | Info
--------|-----------|----------------|----------------|----------|--------|-----------------------------------
...     | ...       | ...            | ...            | ...      | ...    | ...
100     | 50.000000 | 192.168.198.11 | 192.168.191.10 | TCP      | 54     | [ACK] Seq=1 Ack=1 Len=0
```
# IDS logs
1. Excessive TCP Connections Alerts
```bash
[**] [1:1000001:1] POTENTIAL SLOWLORIS ATTACK DETECTED [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
03/10-12:34:56.789012 192.168.198.11:12345 -> 192.168.191.10:1883
TCP TTL:64 TOS:0x0 ID:54321 IpLen:20 DgmLen:52 DF
***A**** Seq: 0x12345678  Ack: 0x87654321  Win: 0x447  TcpLen: 32
TCP Options (3) => NOP NOP TS: 123456789 0
```
2. Alerts for Unusually Long TCP Connections
```bash
[**] [1:1000002:1] UNUSUALLY LONG TCP CONNECTION [**]
[Classification: Potential Denial of Service] [Priority: 2]
03/10-12:35:10.123456 192.168.198.11:23456 -> 192.168.191.10:1883
TCP TTL:64 TOS:0x0 ID:12345 IpLen:20 DgmLen:52
***A**** Seq: 0x23456789 Ack: 0x98765432 Win: 0x448 TcpLen: 32
TCP Options (3) => NOP NOP TS: 234567890 0
```
3. Multiple Reconnection Attempts
```bash
[**] [1:1000003:1] MULTIPLE CONNECTION ATTEMPTS [**]
[Classification: Attempted Denial of Service] [Priority: 2]
03/10-12:36:00.123456 192.168.198.11:34567 -> 192.168.191.10:1883
TCP TTL:64 TOS:0x0 ID:23456 IpLen:20 DgmLen:52 DF
S****** Seq: 0x3456789A Ack: 0x0 Win: 0x449 TcpLen: 32
```
# CPU, RAM and Bandwidth Usage
```bash
Service: CPU Load
State: WARNING
Details: 5-minute load average is at 1.5
Client ID: Attacker_Client_001
Comment: CPU load has increased moderately. Typically, the load average stays around 0.5 under normal operation.
```
```bash
Service: Memory Usage
State: CRITICAL
Details: 85% of RAM is in use.
Client ID: Attacker_Client_001
Comment: RAM usage has significantly increased from an average usage of 45%. Monitor for potential memory exhaustion.
```
```bash
Service: Network Bandwidth
State: OK
Details: Incoming bandwidth usage increased to 200 Kbps from an average of 50 Kbps.
Client ID: Attacker_Client_001
Comment: Slight increase in incoming bandwidth usage. This may indicate numerous new connections but does not yet impact overall network performance significantly.