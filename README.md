# 🦀 Rusty Load Balancer

> **Status:** Active Development (WIP)
> **Focus:** High-Performance Networking, Memory Safety, and Zero-Cost Abstractions.

## 🚀 Overview
**RustyLB** is a Layer 4 (TCP) Load Balancer written from scratch in **Rust**.
The goal of this project is to explore low-level network programming, concurrency models without garbage collection, and the **Tokio** asynchronous runtime.

Unlike standard solutions like NGINX, this project aims to demonstrate how **Memory Safety** principles can prevent common vulnerabilities (buffer overflows) in critical infrastructure components.

## 🏗️ Architecture
The system uses an event-driven architecture powered by `epoll` (via Tokio).

```mermaid
graph LR
    Client[Clients] -- TCP Connection --> Listener[Tokio TCP Listener]
    Listener -- Spawn Task --> Handler[Connection Handler]
    Handler -- Round Robin --> Backend1[Backend Service 1]
    Handler -- Round Robin --> Backend2[Backend Service 2]
