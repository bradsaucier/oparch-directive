[![CI](https://github.com/bradsaucier/OpArch-Directive/actions/workflows/ci.yml/badge.svg)](https://github.com/bradsaucier/OpArch-Directive/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

# Draw It or Lose It: A Strategic Design Directive

**Author**  
Bradley Saucier, SMSgt, USAF (Ret.)  
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

Supported unit: The Gaming Room.  
Mission objective: Expand Draw It or Lose It from a single-platform Android game into a cross-platform, web-based application capable of running on any modern browser and device. The system must support multiple teams and players with unique identifiers, operate in real time, enforce a single authoritative game instance in memory, and maintain speed, security, and consistency across all operating environments.

**2. Strengths in Documentation Development**

I approached the SDD as an operational order. The Recommendations section was built with precision and clarity, leaving no ambiguity in execution. The architecture plan specified a containerized Java backend on Ubuntu Server 24.04 LTS, backed by PostgreSQL for structured data and MinIO for object storage. The communication plan separated control traffic (REST) from real-time updates (WebSockets). Security, scaling, and memory management were detailed to prevent mission drift. Like a mission brief to a pilot, the document provides both the strategic intent and the tactical details required for flawless execution.

**3. The Utility of the Design Document Process**

The design document served as the equivalent of a pre-mission plan. It forced deliberate consideration of constraints, dependencies, and contingencies before execution. By mapping out architecture, data flows, and security posture in advance, the risk of mid-operation surprises was reduced. Just as in operational planning, every line in the document was about controlling the battlespace before contact - allocating resources, defining comms, and ensuring synchronization before code was written.

**4. Proposed Revisions**

The System Architecture View section needs reinforcement. It currently functions as a high-level foundation; in future iterations, I would add detailed diagrams and flow charts to illustrate inter-component communication under various operational scenarios. This would give the development team an even clearer picture of the timing, dependencies, and control paths.

**5. Translating User Needs into Design**

The Gaming Room’s intent for increased market reach and platform flexibility was translated into a PWA deployment model, ensuring broad accessibility without sacrificing performance or security. Requirements like “unique names” became database-level constraints; “real-time play” translated to a WebSocket layer; “security” resulted in end-to-end TLS, short-lived tokens, and OWASP ASVS Level 2 alignment. This is no different from taking a ground commander’s intent and turning it into precise coordinates, ingress/egress plans, and weapons release parameters - failure to translate intent correctly equals mission failure.

**6. Design Approach and Future Strategy**

My approach followed a structured, top-down methodology: executive summary, requirements, constraints, architecture, domain model, evaluation, and recommendations. This mirrors the formal military planning process - establish the objective, assess the battlespace, plan the maneuver, and define sustainment. For future operations, I would integrate rapid prototyping of high-risk components early in the cycle, similar to a ROC drill, to validate design assumptions and catch integration risks before committing full resources.

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
