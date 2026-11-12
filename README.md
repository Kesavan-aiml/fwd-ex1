# EX01 Developing a Simple Webserver
## Date: 3/11/2026
## Reg no: 26018039

## AIM:
To develop a simple webserver to serve html pages and display the list of protocols in TCP/IP Protocol Suite.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Import the necessary modules.

### Step 5:
Define a custom request handler.

### Step 6:
Start an HTTP server on a specific port.

### Step 7:
Run the Python script to serve web pages.

### Step 8:
Serve the HTML pages.

### Step 9:
Start the server script and check for errors.

### Step 10:
Open a browser and navigate to http://127.0.0.1:8000 (or the assigned port).

## PROGRAM:
~~~
from http.server import HTTPServer, BaseHTTPRequestHandler
content = """

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TCP/IP Protocol Suite</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    padding: 24px;
    font-family: "Segoe UI", Arial, sans-serif;
    color: #17233b;
    background: linear-gradient(135deg, #eef4ff, #f8faff, #eaf7f6);
    display: flex;
    align-items: center;
    justify-content: center;
}

.page {
    width: min(1180px, 100%);
}

header {
    text-align: center;
    margin-bottom: 20px;
}

.eyebrow {
    display: inline-block;
    padding: 6px 13px;
    border-radius: 30px;
    background: #e1eaff;
    color: #3159a5;
    font-size: 12px;
    font-weight: bold;
    letter-spacing: 1.4px;
    text-transform: uppercase;
}

h1 {
    margin: 10px 0 5px;
    font-size: 36px;
}

.subtitle {
    margin: 0;
    color: #62708a;
    font-size: 15px;
}

.grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
}

.layer {
    background: white;
    border: 1px solid #dfe7f2;
    border-radius: 15px;
    padding: 17px 19px;
    box-shadow: 0 7px 20px rgba(35,62,105,0.07);
    min-height: 205px;
    position: relative;
    overflow: hidden;
}

.layer::before {
    content: "";
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 5px;
    background: var(--accent);
}

.layer-head {
    display: flex;
    align-items: center;
    gap: 11px;
    margin-bottom: 10px;
}

.number {
    width: 34px;
    height: 34px;
    display: grid;
    place-items: center;
    border-radius: 10px;
    background: var(--soft);
    color: var(--accent);
    font-weight: 800;
}

h2 {
    margin: 0;
    font-size: 19px;
}

.purpose {
    margin: 0 0 12px;
    color: #64718a;
    font-size: 13px;
}

.protocols {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
}

.tag {
    background: var(--soft);
    color: #293a58;
    border: 1px solid var(--line);
    border-radius: 7px;
    padding: 6px 9px;
    font-size: 12.5px;
    font-weight: 650;
}

.tag small {
    color: #66758e;
    font-weight: 500;
}

.application {
    --accent: #3868c8;
    --soft: #edf3ff;
    --line: #dce7ff;
}

.transport {
    --accent: #168b83;
    --soft: #e8f8f5;
    --line: #d1eee8;
}

.internet {
    --accent: #8756bd;
    --soft: #f4edfb;
    --line: #e8daf5;
}

.access {
    --accent: #c07827;
    --soft: #fff4e7;
    --line: #f5e3ca;
}

footer {
    text-align: center;
    margin-top: 15px;
    color: #758199;
    font-size: 11.5px;
}

footer strong {
    color: #53627c;
}

@media (max-width: 700px) {
    body {
        padding: 16px;
        align-items: flex-start;
    }

    .grid {
        grid-template-columns: 1fr;
    }

    .layer {
        min-height: auto;
    }
}

@media print {
    body {
        background: white;
        padding: 10mm;
    }

    .layer {
        box-shadow: none;
    }
}
</style>
</head>

<body>

<main class="page">

<header>
    <span class="eyebrow">Computer Networks</span>
    <h1>TCP/IP Protocol Suite</h1>
    <p class="subtitle">
        List of protocols grouped according to the four layers
    </p>
</header>

<section class="grid">

<!-- Application Layer -->
<article class="layer application">

    <div class="layer-head">
        <span class="number">04</span>
        <h2>Application Layer</h2>
    </div>

    <p class="purpose">
        Provides network services directly to user applications.
    </p>

    <div class="protocols">
        <span class="tag">HTTP – Web</span>
        <span class="tag">HTTPS – Secure Web</span>
        <span class="tag">FTP – File Transfer</span>
        <span class="tag">SMTP – Sending Email</span>
        <span class="tag">POP3 / IMAP – Receiving Email</span>
        <span class="tag">DNS – Name Lookup</span>
        <span class="tag">DHCP – IP Assignment</span>
        <span class="tag">SNMP – Network Management</span>
        <span class="tag">SSH / Telnet – Remote Access</span>
        <span class="tag">NTP – Time Sync</span>
    </div>

</article>

<!-- Transport Layer -->
<article class="layer transport">

    <div class="layer-head">
        <span class="number">03</span>
        <h2>Transport Layer</h2>
    </div>

    <p class="purpose">
        Provides communication between applications on different devices.
    </p>

    <div class="protocols">
        <span class="tag">TCP – Reliable Delivery</span>
        <span class="tag">UDP – Fast, Connectionless Delivery</span>
        <span class="tag">SCTP – Message Transport</span>
    </div>

</article>

<!-- Internet Layer -->
<article class="layer internet">

    <div class="layer-head">
        <span class="number">02</span>
        <h2>Internet Layer</h2>
    </div>

    <p class="purpose">
        Handles logical addressing, packet routing and network control.
    </p>

    <div class="protocols">
        <span class="tag">IPv4 / IPv6 – Addressing and Routing</span>
        <span class="tag">ICMP / ICMPv6 – Error Reporting</span>
        <span class="tag">IGMP – Multicast Groups</span>
        <span class="tag">IPsec – IP Security</span>
    </div>

</article>

<!-- Network Access Layer -->
<article class="layer access">

    <div class="layer-head">
        <span class="number">01</span>
        <h2>Network Access Layer</h2>
    </div>

    <p class="purpose">
        Moves data across the local network and physical medium.
    </p>

    <div class="protocols">
        <span class="tag">Ethernet – Wired LAN</span>
        <span class="tag">Wi-Fi (802.11) – Wireless LAN</span>
        <span class="tag">PPP – Point-to-Point Link</span>
        <span class="tag">ARP – Finds MAC Address</span>
    </div>

</article>

</section>

<footer>
    <strong>Remember:</strong>
    Data moves from the Application Layer down to the
    Network Access Layer during transmission.
</footer>

</main>

</body>
</html>

"""
class myhandler(BaseHTTPRequestHandler):
    def do_GET(self):
        print("request received")
        self.send_response(200)
        self.send_header('content-type', 'text/html; charset=utf-8')
        self.end_headers()
        self.wfile.write(content.encode())
server_address = ('',860)
httpd = HTTPServer(server_address,myhandler)
print("my webserver is running...")
httpd.serve_forever()
~~~

## OUTPUT:
![alt text](<Screenshot 2026-11-03 135136.png>)
![alt text](<Screenshot 2026-11-03 135206.png>)

## RESULT:
The program for implementing simple webserver is executed successfully.

