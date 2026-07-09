# DNS Server 

A simple DNS server written in Python 3. This project demonstrates the core concepts of DNS resolution and server implementation.


## Description 

This repository contains a basic DNS server implemented in Python 3. It's designed to handle DNS queries and resolve domain names by reading zone files. The server listens on UDP port 53 and processes incoming DNS requests.

## Features 

- **DNS Resolution:** Capable of resolving A records for specified domains.
- **Zone File Loading:** Reads domain information from JSON-formatted zone files.
- **UDP Server:** Operates over UDP, the standard protocol for DNS.
- **Customizable IP Binding:** Allows binding to a specific IP address.

## Tech Stack 

- **Language:** Python 3
- **Protocols:** UDP, DNS
- **Data Format:** JSON (for zone files)

## Project Structure 

```
DNS_Server/
├── README.md
└── DNS-master/
    ├── dns.py
    └── zones/
        ├── yahoo.com.zone
        └── youtube.com.zone
```

## Installation 

This project is a standalone Python script and does not have external dependencies beyond Python's built-in libraries.

1. **Clone the repository:**
   ```bash
   git clone https://github.com/avi-vyas/DNS_Server.git
   cd DNS_Server
   ```
2. **Prepare Zone Files:**
   Ensure your zone files are correctly formatted in the `DNS-master/zones/` directory. Each zone file should be a JSON object with a `$origin` key specifying the domain name and other keys for record types (e.g., `a` for A records).

   *Example `yahoo.com.zone` structure (simplified):
   ```json
   {
     "$origin": "yahoo.com",
     "a": [
       {
         "ttl": 3600,
         "value": "192.0.2.1"
       }
     ]
   }
   ```

## Usage 

The DNS server can be started by running the main Python script.

1. **Navigate to the script directory:**
   ```bash
   cd DNS-master
   ```
2. **Run the DNS server:**
   ```bash
   python3 dns.py
   ```

The server will start listening on UDP port 53 for DNS queries. You can then configure clients (e.g., your local machine's network settings) to use this server's IP address (`192.168.236.73` as specified in the code) as their DNS resolver.

## How to Use 
To test the DNS server, you can use tools like `dig` or `nslookup` from another machine configured to use your DNS server's IP address. 

1. **Configure a client to use the server's IP:** Set your client's DNS server to `192.168.236.73`.
2. **Perform a DNS query:**
   ```bash
   dig @192.168.236.73 yahoo.com
   ```
   or
   ```bash
   nslookup yahoo.com 192.168.236.73
   ```

The server should respond with the IP address defined in the `yahoo.com.zone` file.
