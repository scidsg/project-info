
# Hush Line - Data Flow Analysis (Read Me) 🗺
###### Last update: 2024-01-05


## Summary:

This [Hush Line Data Flow Analysis diagram](https://github.com/scidsg/project-info/blob/main/hush-line/8.%20Data%20Modelization/HushLine_DataFlow_20231222.drawio.png) is intended as a tool to help better visualize Hush Line's collection points, protections, and transit protocols used for each piece of sensitive data to help mitigating potential vulnerabilities and exposure within its scope.

## Work in Progress:

It is a work in progress in the sense that it does not include all data outside of its scope, and it could be useful to add some of this information later on in relationship to the sensitive data within its scope. This diagram should also evolve with every change made to the Hush Line system in order to remain accurate and beneficial.

>### Important Notice:

>Not all data within the system is represented on this diagram. Some data isn't sensitive in this context and some is collected by third-party services. For example, the _Receiver_'s IP Address can be known to the system or third-parties without any additional risk to the Sender. The Receiver's identity can, and should, be known publicly. However, the _Sender's_ IP Address is a very important piece of sensitive data to protect within the Hush Line system.

## Definitions of Terms Used and References:

**Sender:** A person or group sending an anonymous tip through the Hush Line system.

**Receiver:** A person or organization managing the email account to receive anonymous tips from the Hush Line system. 

**Server Admin:** A person, group, or third-party organization managing the Hush Line local or virtual server. This person or organization might be different from the Receiver. 

**Authentication Service:** A service or product used to store authentication credentials (identifiers, passwords, secondary factors). This could mean a password manager application, a security token, or any other tool used to store or share authentication credentials.
___

**Tor Network:** A free and open-source software for enabling anonymous communication. It directs Internet traffic via a free, worldwide, volunteer overlay network that consists of more than seven thousand relays. _Source: [https://en.wikipedia.org/wiki/Tor_(network)](https://en.wikipedia.org/wiki/Tor_(network))_

**Tor Browser:** A special privacy-focused browser capable of accessing the Tor Network.

**Tor-Only:** The Hush Line Tor-Only install refers to the installation setup to create and provide access to a version of a custom Hush Line website accessible through the Tor Network using the Tor Browser. Note that Hush Line can also be installed as a mix installation with both an onion website (accessible through Tor) and a public website.

**Onion Service Protocol:** A special protocol used by Tor to improve security and privacy. _More information here: [https://community.torproject.org/onion-services/overview](https://community.torproject.org/onion-services/overview)_

**VPN:** A Virtual Private Network works by creating a secure “tunnel” between your device and your VPN provider, and it protects you in two key ways: 1) Concealing your IP address, protecting your identity and location. 2) Encrypting your traffic between you and your VPN provider so that no one on your local network can decipher or modify it. _Source: [https://www.mozilla.org/products/vpn/resource-center/what-is-a-vpn](https://www.mozilla.org/products/vpn/resource-center/what-is-a-vpn)_
___

**ISP:** An Internet Service Provider. This could mean a provider for an internet service at home, at work, at a cafe, at a library, for a mobile device, etc.

**IP Address:** An Internet Protocol address is a numerical label such as 192.0.2.1 that is used to facilitate communication from a computer network. An IP Address can be used to know the approximate location of a user's network. It can also in some circumstances identify a user directly through their ISP. _More information here: [https://en.wikipedia.org/wiki/IP_address](https://en.wikipedia.org/wiki/IP_address)_

**Nginx:** Nginx is a high-performance and scalable server that can serve HTTP, mail, and TCP/UDP requests. It supports various features such as caching, load balancing, SSL, TLS, filters, and scripting languages. _Source: [https://nginx.org](https://nginx.org)_

**HTTPS:** The Hypertext Transfer Protocol Secure is the secured version of HTTP. It uses encryption for secure communication over a computer network, and is widely used on the Internet. _Source: [https://en.wikipedia.org/wiki/HTTPS](https://en.wikipedia.org/wiki/HTTPS)_

**POST:** A request method supported by HTTP used by the World Wide Web. By design, the POST request method requests that a web server accept the data enclosed in the body of the request message, most likely for storing it. It is often used when uploading a file or when submitting a completed web form. _Source: [https://en.wikipedia.org/wiki/POST\_(HTTP)](https://en.wikipedia.org/wiki/POST_(HTTP))_

**SMTP:** The Simple Mail Transfer Protocol is an Internet standard communication protocol for electronic mail transmission. Mail servers and other message transfer agents use SMTP to send and receive mail messages. _Source: [https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)_
___

**Mailvelope:** Mailvelope is a browser add-on that you can use in Chrome, Edge and Firefox to securely encrypt your emails with PGP using webmail providers. _Source: [https://mailvelope.com](https://mailvelope.com)_

**Maivelope Extension:** Mailvelope adds missing encryption and decryption features to the user interface of common webmail providers. It supports the PGP encryption standard (OpenPGP, GPG) and is compatible with other PGP applications. Encrypt files on your hard drive with Mailvelope and send encrypted email attachments. _Source: [https://addons.mozilla.org/firefox/addon/mailvelope](https://addons.mozilla.org/firefox/addon/mailvelope)_

**PGP Encryption:** Pretty Good Privacy (PGP) is an encryption program that provides cryptographic privacy and authentication for data communication. PGP is used for signing, encrypting, and decrypting texts, e-mails, files, directories, and whole disk partitions and to increase the security of e-mail communications. Phil Zimmermann developed PGP in 1991. _Source: [https://en.wikipedia.org/wiki/Pretty_Good_Privacy](https://en.wikipedia.org/wiki/Pretty_Good_Privacy)_

**GnuPG Program:** GnuPG is a complete and free implementation of the OpenPGP standard as defined by RFC4880 (also known as PGP). GnuPG allows you to encrypt and sign your data and communications; it features a versatile key management system, along with access modules for all kinds of public key directories. _Source: [https://gnupg.org](https://gnupg.org)_



















