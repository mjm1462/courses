cat http.log | grep "GET"
192.168.1.10 - - [01/Apr/2026:09:15:22] "GET /index.html" 200 1024
192.168.1.15 - - [01/Apr/2026:09:15:25] "GET /api/users" 500 312
192.168.1.10 - - [01/Apr/2026:09:16:01] "GET /dashboard" 200 4096
192.168.1.15 - - [01/Apr/2026:09:17:00] "GET /api/users" 500 312
192.168.1.20 - - [01/Apr/2026:09:17:30] "GET /about" 404 128


cat http.log | sed s"/192.168.1.10/LAN(10)/" | sed s"/192.168.1.15/LAN(15)/" | sed s"/10.0.0.5/WAN(5)/" | sed s"/192.168.1.20/LAN(20)/"
LAN(10) - - [01/Apr/2026:09:15:22] "GET /index.html" 200 1024
LAN(15) - - [01/Apr/2026:09:15:25] "GET /api/users" 500 312
WAN(5) - - [01/Apr/2026:09:15:30] "POST /login" 401 215
LAN(10) - - [01/Apr/2026:09:16:01] "GET /dashboard" 200 4096
WAN(5) - - [01/Apr/2026:09:16:05] "POST /login" 401 215
WAN(5) - - [01/Apr/2026:09:16:12] "POST /login" 200 512
LAN(15) - - [01/Apr/2026:09:17:00] "GET /api/users" 500 312
LAN(20) - - [01/Apr/2026:09:17:30] "GET /about" 404 128


cat http.log | awk '{print "Ipv4 Address: " $1}'

Ipv4 Address: 192.168.1.10
Ipv4 Address: 192.168.1.15
Ipv4 Address: 10.0.0.5
Ipv4 Address: 192.168.1.10
Ipv4 Address: 10.0.0.5
Ipv4 Address: 10.0.0.5
Ipv4 Address: 192.168.1.15
Ipv4 Address: 192.168.1.20
