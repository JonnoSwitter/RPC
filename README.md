# 远程过程调用 (RPC) 小项目

## 1. 什么是 RPC？
在现代分布式系统中，随着**微服务架构**的普及和系统复杂度的提升，服务间的通信已成为架构设计的核心挑战。

传统的“本地函数调用”在分布式场景下无法直接应用，因为服务往往运行在不同的物理机器、容器或网络环境中。**远程过程调用 (Remote Procedure Call, RPC)** 应运而生，它的核心目标是**屏蔽底层网络细节**，让开发者调用远程服务时，能像调用本地函数一样简单透明。

---

## 2. 服务端、zookeeper、客户端的主要内容
服务端：
<img width="1482" height="261" alt="image" src="https://github.com/user-attachments/assets/8ac04b2f-a6f4-4247-b2e8-3f455c023519" />
Zookeeper:
<img width="1194" height="302" alt="image" src="https://github.com/user-attachments/assets/cf5b191b-3d88-494c-8213-840447700749" />
客户端：
<img width="1535" height="438" alt="image" src="https://github.com/user-attachments/assets/fa428ae2-57cc-4295-a8a7-2dcf9f2c3df8" />

---

## 3. 技术栈与核心组件
构建一个完备的 RPC 框架需要整合从底层网络 IO 到高层服务治理的多种技术：

### 🌐 网络通信层
* **Socket API 编程**：网络通信的最底层实现基础。
* **异步非阻塞 I/O (epoll)**：利用 Linux 内核的高并发处理能力，提升吞吐量。
* **网络库**：基于Mudo-Reactor 模式的高性能网络框架，优化连接管理,Mudo库建议学习一下，其在高并发场景下使用广泛。

### 📦 协议与序列化
* **网络协议**：基于 **TCP/UDP** 的传输。
* **Protobuf (Protocol Buffers)**：高效的二进制序列化方案，确保数据在网络传输中体积更小、解析更快。

### ⚖️ 服务治理
* **服务注册与发现 (Zookeeper)**：解决分布式环境下服务地址动态变更的问题，实现负载均衡。
* **gRPC 框架**：集成了 Protobuf 与 HTTP/2 的 RPC 解决方案。

---
## 4.测试结果
经本地模拟客户端与服务端进行测试，可实现万次级服务请求得到正常响应。（实测结果保存在img目录下）
