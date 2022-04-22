---
uid: PIAdapterForDNP3Security
---

# Security 

When determining DNP3 security practices with regards to REST APIs, you should consider the following practice. To keep the adapter secure, only administrators should have access to machines where the adapter is installed. REST APIs are bound to localhost, meaning that only requests coming from within the machine will be accepted. 

## DNP3 protocol

The DNP3 adapter does not currently support transport layer security between the adapter and the data source, which means that DNP3 traffic will be unprotected. If needed, use other measures to protect this traffic, such as a VPN connection, air-gapped control network, or SSH tunnel. 
