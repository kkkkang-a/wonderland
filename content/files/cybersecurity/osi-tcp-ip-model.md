---
title: Open Systems Interconnection (OSI) Model and TCP/IP Model
---

# OSI Model

The OSI model is a conceptual model used to characterise and standardise how the different software and hardware components involved in network communication should be divided and interact with each other.

It has seven layers (from high to low): physical layer, data link layer, network layer, transport layer, session layer, representation layer, and application layer.

## 7 Layers in the OSI Model

### Physical Layer

The physical layer defines the electrical and physical specifications for data connections. It is responsible for transmitting and receiving unstructured raw data in physical media. Bit rate control is done at the physical layer. It is the low-level network device layer and is never concerned with protocols or other high-level items.

Examples include the pinouts of connectors, the operating voltage of cables, the specifications of fibre optic cables, and the frequencies of wireless devices.

>[!NOTE] Summary
>- 提供建立、维护和释放物理链路所需的机械、电气功能和规程等特性
>- 通过传输介质进行数据流(比特流)的物理传输、故障监测和物理层管理
>- 从数据链路层接收帧，将比特流转换成底层物理介质上的信号

### Data Link Layer

The data link layer provides node-to-node transmission. It defines protocols for establishing and terminating connections between two physically connected devices.

The data link layer is generally divided into two sublayers:
- The Media Access Control (MAC) layer is responsible for controlling how devices in the network are granted access to the media and the authority to transmit data.
- The Logical Link Control (LLC) layer is responsible for identifying and encapsulating the network-layer protocols, and controlling error checking and frame synchronisation.

>[!NOTE] Summary
>- 在物理链路的两端之间传输数据
>- 在网络层实体间提供数据传输功能和控制
>- 提供数据的流量控制
>- 检测和纠正物理链路产生的差错

### Network Layer

The network layer is responsible for host addressing, packaging, and routing functions. The core protocols of the layer are:
- [Internet Protocol (IP)](ip.md) is a routable protocol responsible for IP addressing, routing, and packet segmentation and reassembly of data packets.
- [Address Resolution Protocol (ARP)](arp.md) is responsible for discovering network access layer addresses, such as hardware addresses associated with a given Internet layer access.
- Internet Control Message Protocol (ICMP) is responsible for providing diagnostics and reporting errors due to unsuccessful IP packet delivery.
- Internet Group Management Protocol (IGMP) is responsible for IP multicast group management.

>[!NOTE] Summary
>- 负责端到端的数据的路由或交换，为传输数据建立连接
>- 寻址并解决与数据在异构网络间传输相关的所有问题
>- 使用上面的传输层和下面的数据链路层的功能

### Transport Layer

The transport layer is responsible for providing session and datagram communication services to the application layer.

The core protocols for this layer are TCP and UDP.
- [Transmission Control Protocol (TCP)](tcp.md) provides one-to-one, connection-oriented, reliable communication services. It is responsible for sequencing and acknowledging packets sent, as well as recovering packets lost in transit.
- [User Datagram Protocol (UDP)](udp.md) provides one-to-one or one-to-many, connectionless, unreliable communication services. UDP is typically used when the amount of data to be transmitted is small (e.g. the data fits into a single packet).

>[!NOTE] Summary
>- 提供无差错的数据传输
>- 接收来自会话层的数据，如果需要，将数据分割成更小的分组，向网络层传送分组并确保分组完整和正确到达它们的目的地
>- 在系统之间提供可靠的透明的数据传输，提供端到端的错误恢复和流量控制

### Session Layer

The session layer controls the connections between computers. It establishes, manages, maintains, and terminates connections between local and remote applications. It also verifies that data has been delivered.

>[!NOTE] Summary
>- 提供节点之间通信过程的协调
>- 负责执行会话规则、同步数据流以及当故障发生时重新建立连接

### Representation Layer

The representation layer examines the data to ensure that it is compatible with the communication resources. It converts the data into a form that is accepted at the application level.

It is also used for data compression and encryption. For example, video calls are compressed during transmission to allow faster transmission and recovery of data at the receiving end. For data with high security requirements, such as text messages containing password, it will be encrypted at this level.

>[!NOTE] Summary
>- 提供数据格式、变换和编码转换
>- 涉及正在传输数据的语法和语义
>- 将消息以合适电子传输的格式编码
>- 执行该层的数据压缩和加密
>- 从应用层接收消息，转换格式，并传送到会话层（常被合并在应用层中）

### Application Layer

The application layer interacts directly with the software application, providing communication functions as needed, closest to the end user.

The functions of the application layer typically include verifying the availability of communication partners and resources to support any data transfer.

This layer also defines protocols for end-use applications such as Domain Name System (DNS), File Transfer Protocol (FTP), Hypertext Transfer Protocol (HTTP), Internet Message Access Protocol (IMAP), Post Office Protocol (POP), Simple Mail Transfer Protocol (SMTP), Simple Network Management Protocol (SNMP), and Telnet (terminal emulation).

>[!NOTE] Summary
>- 包括各种协议，它们定义了具体的面向用户的应用：如电子邮件、文件传输等

## Support Layers: User and Network

In the OSI model, the user support layer includes session layer, representation layer and application layer. It is mainly concerned with ensuring that information is transmitted in a correctly understandable form.

The network support layer includes physical layer, data link layer and network layer. It deals with the physical aspects of moving data from one device to another. It is responsible for error-free and orderly delivery of data, and its processing functions include error control, flow control, routing, and network interconnection.

The transport layer is the interface between the higher and lower three layers, and it is the first end-to-end layer that guarantees transparent end-to-end connectivity, meets the [quality of service (QoS)](qos.md) requirements of the users, and provides the appropriate form of information to the higher three layers.

## Data Encapsulation

Each layer in the sending device adds its own information to the message (or package) it, receives from the layer just above it and passes the whole package to the layer just below it.

At the receiving machine, the message is unwrapped layer by layer, with each process receiving and removing the data meant for it. 

Each interface defines the information and services a layer must provide for the layer above it.

# TCP/IP Model

Comparing the layers of the TCP/IP model and the OSI model, the application layer in the TCP/IP protocol suite is a combination of three layers in the OSI model: application layer, presentation layer and session layer. This is because the TCP/IP model is more simplified and streamlined, focusing on the most critical aspects of the network communication.

Reasons:
- Some of the functionalities of the session layers are available in some of the transport layer protocols.
- Applications and protocols at the application layer in the TCP/IP model can handle specific tasks related to data formatting, encryption, and session management as needed, without the need for separate layers.