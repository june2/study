# How Does DNS Work?

1. A check is made to see if the details of that name are known locally, e.g., if the browser has made a previous request from that same domain name or there is an entry in the local DNS registry (e.g., hosts.txt on Windows).

2. If no local record is found, a request is sent to your local DNS server. This could be running locally on your machine or on an office network, but most commonly it is provided by the ISP that supplies your internet connection.

3. The local DNS server again checks if it already has the details of the name being requested. If there is no cached record, then the DNS server needs to locate the details of the name server that hosts the domain record for the address you are trying to resolve (the authoritative domain name server).

4. To do this the DNS server breaks the name down into its different sections, starting from the righthand side of the domain name. For example, for www.google.com, this would be split into com, google, and www. The section after the final . of the domain name (in this case, com) is known as the top-level domain (TLD). A root name server is connected to find details of the server that holds the domain record for the TLD.

5. The DNS server will make a request to the TLD name servers asking for details of the name servers that contain the details of the next section of the domain name (in this example, google). The DNS server then makes a request to the name server that holds the details for google.com. This name server may then return details of another name server that holds the records for www.google.com or, more likely at this point, will return the address associated with www.google.com.

6. The address returned by the remote name server can be an IP address or it could be another domain name, known as a CNAME; for example, www.google.com may return a reference to cdn-us.aa1.google-us.com.

7. If a CNAME is returned, the DNS server then repeats the process with the CNAME until an IP address is resolved.


An example of a recursive DNS process is shown below.


![image](https://user-images.githubusercontent.com/5827617/55053791-a71a0300-50a0-11e9-905c-277da3b54b10.png)




# DNS Types: 3 Types of DNS Servers
The following are the most common DNS server types that are used to resolve hostnames into IP addresses.

### DNS Resolver
A DNS resolver (recursive resolver), is designed to receive DNS queries, which include a human-readable hostname such as “www.example.com”, and is responsible for tracking the IP address for that hostname.

### DNS Root Server
The root server is the first step in the journey from hostname to IP address. The DNS Root Server extracts the Top Level Domain (TLD) from the user’s query — for example, www.example.com — and provides details for the .com TLD Name Server. In turn, that server will provide details for domains with the .com DNS zone, including “example.com”.

There are 13 root servers worldwide, indicated by the letters A through M, operated by organizations like the Internet Systems Consortium, Verisign, ICANN, the University of Maryland, and the U.S. Army Research Lab.

### Authoritative DNS Server
Higher level servers in the DNS hierarchy define which DNS server is the “authoritative” name server for a specific hostname, meaning that it holds the up-to-date information for that hostname.

The Authoritative Name Server is the last stop in the name server query—it takes the hostname and returns the correct IP address to the DNS Resolver (or if it cannot find the domain, returns the message NXDOMAIN).


# DNS Types: 10 Top DNS Record Types
DNS servers create a DNS record to provide important information about a domain or hostname, particularly its current IP address. The most common DNS record types are:

- Address Mapping record (A Record)—also known as a DNS host record, stores a hostname and its corresponding IPv4 address.

- IP Version 6 Address record (AAAA Record)—stores a hostname and its corresponding IPv6 address.

- Canonical Name record (CNAME Record)—can be used to alias a hostname to another hostname. When a DNS client requests a record that contains a CNAME, which points to another hostname, the DNS resolution process is repeated with the new hostname.

- Mail exchanger record (MX Record)—specifies an SMTP email server for the domain, used to route outgoing emails to an email server.

- Name Server records (NS Record)—specifies that a DNS Zone, such as “example.com” is delegated to a specific Authoritative Name Server, and provides the address of the name server.

- Reverse-lookup Pointer records (PTR Record)—allows a DNS resolver to provide an IP address and receive a hostname (reverse DNS lookup).

- Certificate record (CERT Record)—stores encryption certificates—PKIX, SPKI, PGP, and so on.

- Service Location (SRV Record)—a service location record, like MX but for other communication protocols.

- Text Record (TXT Record)—typically carries machine-readable data such as opportunistic encryption, sender policy framework, DKIM, DMARC, etc.

- Start of Authority (SOA Record)—this record appears at the beginning of a DNS zone file, and indicates the Authoritative Name Server for the current DNS zone, contact details for the domain administrator, domain serial number, and information on how frequently DNS information for this zone should be refreshed.
