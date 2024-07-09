We specify the nodes of a [[Computer Network|computer network]] by *naming*, i.e., giving a name to every node. Therefore, every network has a *namespace*, which consists of all names of the network specified by a naming scheme.

Examples of Naming Schemes:

| Namespace     | Instance          | Remark                                       |
| ------------- | ----------------- | -------------------------------------------- |
| Personal Name | Joan Smith        | Personal names in a country                  |
| WeChat User   | `HappyDog`        | Any legitimate string per WeChat standard    |
| URL           | www.google.com    | Universal Resource Locator of a webpage      |
| Email address | bob@gmail.com     | `userName@domainName`                        |
| IP Address    | 159.226.97.84     | Internet protocol address per IETF standards |
| Phone number  | 189-6666-8888     | Decimal digits by Telcom provider standards  |
| MAC address   | 00-1E-C9-43-24-42 | 12 hexadecimal digits per IEEE standards     |
A name is usually a string of characters. Whether a string is legitimate is determined by a naming scheme, which is often specified by some technical standard. Designing a namespace needs to consider the following issues:

- **Uniqueness**. Does a name map to a unique node? The email address namespace enjoys uniqueness, but the namespace of personal names of a country’s population does not have uniqueness. There may be multiple persons named Joan Smith, causing name conflicts, which in turn may lead to wrong connections.
- **Autonomy**. Can a user create or change a name on his own? Such autonomy has the advantage of convenience, but may lead to chaos. One may change a URL, i.e., the name of a webpage. However, Web links to the old URL become invalid. For many naming schemes, creating or modifying a name need to go through a centralized process, involving an authority of name registry.
- **Friendliness**. Are the names user-friendly, i.e., understandable by humans? “Joan Smith” is much more understandable than the MAC address  “00-1E-C9-43-24-42”

# Domains vs IPs
An *IP (Internet Protocol) address* is a unique numerical identifier assigned to each device connected to the internet. IP addresses come in two main versions:
1. **IPv4**: These are 32-bit addresses typically represented as four groups of numbers separated by dots, such as 192.168.1.1.
2. **IPv6**: These are 128-bit addresses represented as eight groups of hexadecimal digits separated by colons, like 2400:cb00:2048:1::c629:d7a2.

A *domain name* is a human-readable address used to identify websites on the internet. It serves as a user-friendly alternative to *IP addresses*, making it easier for people to remember and access websites. For example, "nytimes.com" and "espn.com" are domain names that users can type into their web browsers to visit specific websites.

The *Domain Name System (DNS)* acts as the "phonebook of the Internet" by translating domain names into IP addresses. When you enter a domain name in your web browser, a DNS lookup process occurs behind the scenes to find the corresponding IP address. This process involves several steps, including querying DNS servers and resolvers to locate the correct IP address for the requested domain.

# The Namespace of the World Wide Web: URL
A *URL(Uniform Resource Locator)* is a standardized address used to locate and access resources on the internet. It typically consists of several parts:
1. **Scheme**: Specifies the protocol to be used (e.g., http, https, ftp)
2. **Hostname**: The domain name or IP address of the server hosting the resource
3. **Path**: Indicates the specific location of the resource on the server
4. **Optional components**: Query parameters and fragments (anchors) for additional information or specific sections of a page

For example, in the URL "https://www.example.com/page?id=123#section1":
- "https" is the *scheme*
- "www.example.com" is the *hostname*
- "/page" is the *path*
- "?id=123" is a *query parameter*
- "#section1" is a *fragment*

Specifically, in the scheme we usually have *HTTP (Hypertext Transfer Protocol)* and *HTTPS (HTTP Secure)* protocols used for transmitting data over the internet.

HTTP is the original protocol for transmitting web content, where data is sent in plain text, making it vulnerable to interception. And HTTPS is secure version of HTTP, which uses encryption (typically *SSL/TLS*) to protect data during transmission. Modern web browsers often warn users when accessing sites using unsecured HTTP connections, encouraging the use of HTTPS for improved security and privacy