# Software Requirements Specification (SRS) — Musical You

## 1. Introduction

**Project Overview:**  
Musical You is a full-stack web application that analyzes Spotify listening data to provide users with interactive analytics dashboards and smart playlist generation. Users gain insights into their listening habits and can discover music based on trends and preferences.

**Purpose of this Document:**  
This SRS defines the functional and non-functional requirements, system constraints, assumptions, external interfaces, and acceptance criteria for Musical You. It serves as a blueprint for development, deployment, and evaluation of the application.

**Intended Audience:**  
- Developers working on the project  
- Recruiters or interviewers evaluating technical depth  
- Stakeholders interested in understanding system functionality

**Definitions / Acronyms:**  
- **MVP** — Minimum Viable Product  
- **OAuth** — Open standard for secure authentication  
- **CI/CD** — Continuous Integration / Continuous Deployment  

---

## 2. Overall Description (System Context)

**Users:**  
- Spotify account holders who want insights and playlists.

**Operational Environment:**  
- **Frontend:** React + TypeScript, running in modern browsers  
- **Backend:** Java Spring Boot REST APIs, running on AWS EC2  
- **Database:** PostgreSQL on AWS RDS  

**System Interactions:**  
- Interacts with Spotify Web API for fetching listening data and creating playlists  
- Frontend communicates with backend via REST API calls  
- Backend stores and retrieves data from PostgreSQL database  

**Assumptions:**  
- Users have a Spotify account  
- Users have a modern browser  
- Internet connectivity is stable  

---

## 3. Specific Requirements

### 3.1 External Interface Requirements
- **Spotify API:** REST endpoints returning JSON; OAuth2 authentication required  
- **Frontend to Backend:** REST API calls, JSON payloads  
- **Database:** PostgreSQL tables (`users`, `tracks`, `artists`, `listening_history`, `playlists`)  

### 3.2 Constraints and Assumptions
**Constraints:**  
- Spotify Web API rate limits (~50 requests/minute per user)  
- OAuth tokens expire every hour  
- AWS RDS instance storage and throughput limitations  
- MVP scope limited to a single-user functional demo  

**Assumptions:**  
- Users are online during data import and playlist generation  
- Single-developer effort for MVP  
- AWS services are available and accessible  

### 3.3 Functional Requirements

| ID | Feature | Description | Priority |
|----|--------|------------|---------|
| FR1 | Spotify OAuth Login | Users can securely log in using Spotify | High |
| FR2 | Data Import | Fetch user listening history and store in database | High |
| FR3 | Analytics Dashboard | Display top tracks, artists, genres, and trends | High |
| FR4 | Playlist Generation | Generate playlists based on user preferences | Medium |
| FR5 | Logout | Revoke tokens and end session securely | Medium |
| FR6 | Error Handling | Handle API failures, expired tokens, and connectivity issues | High |

### 3.4 Non-Functional Requirements

| ID | Requirement | Description |
|----|------------|------------|
| NFR1 | Security | OAuth tokens stored securely, HTTPS enforced |
| NFR2 | Performance | Dashboard queries return results <2 seconds for typical users |
| NFR3 | Scalability | Support multiple users in future without performance degradation |
| NFR4 | Maintainability | Modular, well-documented code |
| NFR5 | Reliability | Retry mechanisms for API calls, logging, and error handling |

---

## 4. Use Cases (User Interaction Scenarios)

| Use Case | Actor | Description |
|----------|-------|-------------|
| Login via Spotify | User | User authenticates via OAuth; system stores access tokens securely |
| View Analytics | User | User views top tracks/artists/genres and listening trends on dashboard |
| Generate Playlist | User | User selects criteria (genre/mood); system generates playlist in Spotify account |

---

## 5. Acceptance Criteria

- User can log in with Spotify account  
- Listening data is imported correctly into the database  
- Analytics dashboard displays accurate charts for top tracks, artists, and genres  
- Playlist generation works based on user-selected criteria  
- Application is deployed and accessible on AWS  

---

## 6. References

- Spotify Web API: [https://developer.spotify.com/documentation/web-api/](https://developer.spotify.com/documentation/web-api/)  
- AWS Free Tier: [https://aws.amazon.com/free/](https://aws.amazon.com/free/)  
- React Documentation: [https://reactjs.org/docs/getting-started.html](https://reactjs.org/docs/getting-started.html)  
- Spring Boot Documentation: [https://spring.io/projects/spring-boot](https://spring.io/projects/spring-boot)  