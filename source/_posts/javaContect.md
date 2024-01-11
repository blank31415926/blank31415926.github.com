---
title: JAVA的通信
label: JAVA
intro: java组件通信
date: 2024-01-12
img:  "../img/test1.png"
---


UDP（User Datagram Protocol）和TCP（Transmission Control Protocol）是两种常见的传输层协议，用于在计算机网络中实现数据传输。

* UDP通信(*数据包通信*)：
UDP是一种**无连接的、不可靠的**传输协议。它提供了一种简单的数据传输机制，适用于一些对数据可靠性要求较低、传输延迟较敏感的应用场景。
UDP通信常用于实时性要求较高的应用，如音频、视频等流媒体传输，以及一些需要快速发送短消息的应用。

* TCP通信(*套接字*)：
TCP是一种面向连接的、可靠的传输协议。它提供了一种面向流的数据传输机制，适用于对数据可靠性要求较高的应用场景。TCP通信的特点包括：

TCP通信适用于需要**可靠传输**的应用，如文件传输、Web浏览器与服务器的通信等。

其次是两个关键类的构建参数
* 创建套接字（Socket）的API参数：

	IP地址：指定目标主机的IP地址，可以是IPv4或IPv6地址。（本机链接时可以省略IP）
	
	端口号：指定与套接字关联的端口号，用于标识应用程序的通信端口。
	
	即 `new Socket(String host, int port)`;
	
* 创建数据包（Packet）的API参数：
	
	数据：要发送的实际数据，通常以字节数组或字符串的形式提供。
	
	数据长度：数据的实际长度。
	
	IP地址：指定目标主机的IP地址，可以是IPv4或IPv6地址。
	
	端口号：指定与数据包关联的端口号，用于标识应用程序的通信端口。
	
`new DatagramPacket(byte[] buf, int length, InetAddress address, int port)`

首先需要指出的是 客户端和服务端 都是 DatagramSocket[^DatagramSocket] 并不会因为服务端是一对多就不一样
客户端A发送一个DatagramPacket[^DatagramPacket] 服务端接收 并将其发送给除了A以外的其他客户端 




[^DatagramSocket]: 可以理解为一个邮局 Socket的意思是插座、基座 构建时

[^DatagramPacket]: 可以理解为一个信封 包含了出发地址 目标地址 数据 `DatagramPacket(sendData, sendData.length, serverAddress, port);`
