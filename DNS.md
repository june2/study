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
