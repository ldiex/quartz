A protocol is a set of rules enabling two nodes of a network to communicate with each other, in order to automatically collaborate in accomplishing a common computational task. A protocol stack is a stack of layers of protocols which work together. This section introduces the Web over Internet protocol stack, to elaborate the basic concepts of communication in a [[Computer Network|computer network]].

# Protocol stack of the OSI model
The OSI (Open Systems Interconnection) model is a conceptual framework used to understand network interactions in seven layers. 

| Layer | Name         | Function                                                        | Examples               |
| ----- | ------------ | --------------------------------------------------------------- | ---------------------- |
| 7     | Application  | Provides network services directly to end-users or applications | HTTP, FTP, SMTP, DNS   |
| 6     | Presentation | Formats and encrypts data for the application layer             | JPEG, MPEG, SSL/TLS    |
| 5     | Session      | Manages sessions between applications                           | NetBIOS, RPC           |
| 4     | Transport    | Provides end-to-end communication and reliability               | TCP, UDP               |
| 3     | Network      | Routes data packets between different networks                  | IP, ICMP, OSPF         |
| 2     | Data Link    | Provides node-to-node communication and error detection         | Ethernet, Wi-Fi, PPP   |
| 1     | Physical     | Transmits raw bit stream over physical medium                   | Cables, Switches, Hubs |
The following example shows the process of fetching a picture from a URL (e.g., `https://www.example.com/pic.png`) 
## Application Layer (Layer 7)
- **Request**: Your web browser sends an HTTP GET request to `https://www.example.com/pic.png`.
- **Response**: The server responds with the image data.

## Presentation Layer (Layer 6)
- **Encryption**: If using HTTPS, SSL/TLS encrypts the data before transmission.

## Session Layer (Layer 5)
- **Session Management**: SSL/TLS session is established and maintained for the duration of the request.

## Transport Layer (Layer 4)
- **Segmentation**: The image data is segmented into smaller chunks (TCP segments).
- **Error Handling**: TCP ensures all segments arrive correctly and reassembles them.

## Network Layer (Layer 3)
- **IP Packetization**: Each TCP segment is encapsulated into an IP packet.
- **Routing**: The IP packet is routed from the source to the destination (web server to client).

## Data Link Layer (Layer 2)
- **Frame Encapsulation**: IP packets are encapsulated into Ethernet frames (or Wi-Fi frames for wireless).
- **MAC Addressing**: Frames are addressed using MAC addresses for local network delivery.

## Physical Layer (Layer 1)
- **Bit Transmission**: Frames are converted into electrical, optical, or radio signals and transmitted over the medium (e.g., copper wire, fiber optic cable, radio waves).

In the physical layer, data is transmitted as a sequence of bits. These bits are grouped and interpreted based on the physical layer protocol. For Ethernet, the frame structure includes:
1. **Preamble**: A sequence of bits used for synchronization.
2. **Start Frame Delimiter (SFD)**: Indicates the start of the frame.
3. **Destination MAC Address**: The MAC address of the receiving device.
4. **Source MAC Address**: The MAC address of the sending device.
5. **Type/Length**: Indicates the type of protocol (e.g., IPv4) or the length of the payload.
6. **Payload**: The actual data being transmitted (e.g., a segment of the image file).
7. **Frame Check Sequence (FCS)**: Used for error checking to ensure data integrity.