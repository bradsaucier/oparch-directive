[![CI](https://github.com/bradsaucier/OpArch-Directive/actions/workflows/ci.yml/badge.svg)](https://github.com/bradsaucier/OpArch-Directive/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

# Draw It or Lose It - Software Design Document

Author  
Bradley Saucier  
B.S. Candidate, Computer Science (STEM Project Management), Southern New Hampshire University  
B.A. Economics, Columbia University  
A.A.S., Community College of the Air Force

- **Purpose**: This repository contains the software design document (SDD) for "Draw It or Lose It," a project for CS 230. It serves as the architectural blueprint and strategic recommendation for evolving the client's software from a single-platform application to a scalable, web-based service.

---

### Mission Context

The client, The Gaming Room, required a strategic plan to expand their existing Android game, "Draw It or Lose It," into a web-based, multi-platform application. The primary objective was to maximize market reach and user engagement by making the game accessible across various devices and operating systems without compromising performance or security.

---

### Mission Plan

This project can be understood through the five-paragraph order format:

- **1. Situation:** The client's asset is confined to the Android ecosystem, limiting its operational reach. Competitors occupy a wider battlespace across web and iOS platforms. The objective is to break out from the current area of operations.

- **2. Mission:** Design a scalable, secure, and cross-platform architecture that enables "Draw It or Lose It" to be deployed as a web-based application, capturing a broader user base and establishing a competitive market position.

- **3. Execution:**
  - **Concept of Operations:** The operation will be executed by designing a three-tier architecture with a Progressive Web App (PWA) client and a containerized Java backend. The backend will serve as the single source of truth, managing game state via a singleton service.
  - **Backend:** Deploy a Java application on Ubuntu Server 24.04 LTS, containerized with Docker and prepared for Kubernetes orchestration.
  - **Frontend:** Develop a PWA with React to ensure maximum compatibility and reach across all target devices (Windows, macOS, iOS, Android).
  - **Comms:** Use a stateless REST API for standard game setup and a WebSocket channel for low-latency, real-time gameplay communication.

- **4. Sustainment:**
  - **Data Persistence:** Utilize PostgreSQL for structured data (accounts, scores) and MinIO for object storage (drawings, avatars).
  - **Logistics:** Implement the 3-2-1 backup strategy to ensure data integrity and disaster recovery.
  - **Maintenance:** Leverage a container-based architecture for simplified updates, scaling, and long-term maintenance. The system is designed for high availability and graceful failure using a Circuit Breaker pattern.

- **5. Command and Signal:**
  - **Command:** The `GameService` class, implemented as a singleton, acts as the central command node for all game logic, ensuring state consistency.
  - **Signal:** All communications between client and server will be encrypted using TLS 1.3. Secure token-based authentication will manage user sessions. The system will be monitored via logs, metrics, and traces to ensure operational awareness.

---

### After-Action Report and Reflection

This section serves as a debrief of the design process, fulfilling the requirements for the CS 230 Module Eight Journal.

**1. Client and Requirements Summary**

- **Client:** The Gaming Room.  
- **Software Requirement:** The client required a software design to evolve their existing single-platform Android game, "Draw It or Lose It," into a scalable, secure, and cross-platform web-based service. The primary objective was to maximize market reach by ensuring accessibility on any device with a modern web browser.

**2. Strengths in Documentation Development**

##TODO

**3. The Utility of the Design Document Process**

##TODO

**4. Proposed Revisions**

##TODO

**5. Translating User Needs into Design**

##TODO

**6. Design Approach and Future Strategy**

##TODO
---

### Deliverables and Directory Layout

- `README.md`: This document.
- `documentation/CS230_Software_Design_Document_TheGamingRoom.pdf`: The primary deliverable containing the full software design and recommendations.
- `.github/`: Contains the CI workflow.
- `LICENSE`: MIT License governing the reuse of this repository's content.
- `REFERENCES.md`: A list of all external standards, specifications, and tools cited in this project.

---

### Academic Integrity and Citation Policy

All work in this repository is my own, completed in accordance with the Southern New Hampshire University Academic Integrity Policy.  
All external sources, standards, and tools that informed the design are cited in the main PDF document and listed in `REFERENCES.md`.

---

### License and Reuse

This project is licensed under the MIT License. See the `LICENSE` file for full details. You are free to use, share, and adapt the content as long as you provide attribution.
