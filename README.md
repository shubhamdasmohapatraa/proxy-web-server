# Multithreaded Proxy Web Server

## 📌 Overview

This project implements a **multithreaded proxy web server** in **C** that can handle multiple concurrent client requests efficiently. The proxy forwards HTTP requests from clients to target servers, relays responses back, and optionally caches responses to improve performance.

The design focuses on **concurrency, synchronization, and performance optimization**, making it suitable as a systems / backend project.

---

## 🚀 Key Features

* **Multithreaded Architecture**

  * Handles multiple client connections concurrently using POSIX threads (pthreads).

* **Thread Synchronization**

  * Uses **mutex locks** and **semaphores** to prevent race conditions and ensure thread-safe access to shared resources.

* **HTTP Request Parsing**

  * Parses and validates HTTP requests using a custom request parser.

* **Optional LRU-Based Caching**

  * Implements a **Least Recently Used (LRU)** cache to store server responses.
  * Reduces response latency and improves throughput under high load.

* **Robust Error Handling**

  * Gracefully handles invalid requests, connection failures, and server errors.

---

## 🛠️ Tech Stack

* **Language:** C
* **Concurrency:** POSIX Threads (pthreads)
* **Synchronization:** Mutexes, Semaphores
* **Networking:** BSD Sockets
* **Caching Policy:** LRU (Least Recently Used)

---

## 📂 Project Structure

```
proxy-web-server/
│── README.md
│── proxy server with cache.c   # Main proxy server implementation
│── proxy_parse.c               # HTTP request parsing logic
│── proxy_parse.h               # Header file for request parser
```

---

## ⚙️ How It Works

1. The proxy server listens on a specified port for incoming client connections.
2. Each client connection is handled by a **separate thread**.
3. Incoming HTTP requests are parsed and validated.
4. If caching is enabled:

   * The proxy checks whether the requested resource exists in cache.
   * On a cache hit, the response is returned immediately.
   * On a cache miss, the request is forwarded to the target server.
5. The server response is relayed back to the client and optionally stored in the cache following the **LRU policy**.

---

## ▶️ Compilation & Execution

### Compile

```bash
gcc -pthread "proxy server with cache.c" proxy_parse.c -o proxy_server
```

### Run

```bash
./proxy_server <PORT_NUMBER>
```

Example:

```bash
./proxy_server 8080
```

Configure your browser or client to use `localhost:8080` as the proxy.

---

## 📈 Performance Benefits

* Supports high concurrency using multithreading
* Reduces network latency via LRU caching
* Efficient synchronization avoids bottlenecks under load

---

## 🧪 Future Improvements

* Support for HTTPS (CONNECT method)
* Configurable cache size and eviction policy
* Logging and monitoring support
* Non-blocking I/O using `epoll` or `select`

---

## 👤 Author

**Shubham Das Mohapatra**

* GitHub: [https://github.com/shubhamdasmohapatraa](https://github.com/shubhamdasmohapatraa)

---

## ⭐ Why This Project Matters

This project demonstrates strong understanding of:

* Operating systems concepts
* Multithreading and synchronization
* Computer networks and HTTP protocol
* Low-level systems programming in C

A solid backend / infrastructure-focused project suitable for system-level and SDE roles.

