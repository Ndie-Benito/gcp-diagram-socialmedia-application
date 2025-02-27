# gcp-diagram-socialmedia-application
Task: Scenario 3: Social Media Application
---

### **1. Presentation Tier (Frontend)**
- **Components**:
  - **Web Browser**: For desktop users accessing the application via a website.
  - **Mobile App**: For mobile users accessing the application via a native app.
- **Technologies**:
  - **Vue.js**: For building a responsive and dynamic web interface.
  - **HTML/CSS/JavaScript**: Core technologies for rendering the UI and handling client-side interactions.
  - **React Native**: For building cross-platform mobile applications (iOS and Android).

---

### **2. Application Tier (Backend)**
- **Components**:
  - **Web Server**: Handles HTTP requests and serves static assets.
  - **API Server**: Manages business logic, processes requests, and interacts with the database.
- **Technologies**:
  - **Go with Gin**: A high-performance framework for building RESTful APIs.
  - **Node.js with Express.js**: A lightweight and scalable framework for handling API requests.
  - **Java with Spring Boot**: A robust framework for building enterprise-grade applications.

---

### **3. Data Tier (Database)**
- **Components**:
  - **Database Server**: Stores persistent data like user profiles, posts, comments, and likes.
  - **Cache Server**: Stores frequently accessed data to improve performance.
- **Technologies**:
  - **MongoDB**: A NoSQL database for storing unstructured or semi-structured data like user posts and comments.
  - **Redis**: An in-memory data store for caching frequently accessed data (e.g., popular posts, user sessions).

---

### **User Interaction Flow**
1. **User Login**:
   - The user logs in via the website or mobile app.
   - The frontend sends the login credentials to the backend for authentication.
   - The backend verifies the credentials and returns a session token or JWT (JSON Web Token) for subsequent requests.

2. **Fetching User Feed**:
   - The frontend requests the user’s feed from the backend.
   - The backend retrieves posts from the database (MongoDB) and checks Redis for cached posts.
   - If cached data is available, it is served directly from Redis for faster response times.
   - If not, the backend queries MongoDB, caches the results in Redis, and sends the feed data to the frontend.

3. **Creating a New Post**:
   - The user creates a new post via the frontend.
   - The frontend sends the post data to the backend.
   - The backend processes the post (e.g., validates content, associates it with the user) and stores it in MongoDB.
   - The backend may also update the cache in Redis if the post is expected to be frequently accessed.

4. **Interacting with Posts**:
   - The user’s friends interact with the post (e.g., like, comment).
   - The frontend sends the interaction data (e.g., like, comment) to the backend.
   - The backend updates the database (MongoDB) to reflect the interaction.
   - The backend may also update the cache in Redis to ensure consistency.

---

### **Key Features and Considerations**
1. **User Authentication**:
   - Use JWT or OAuth for secure authentication.
   - Store session data in Redis for quick access and scalability.

2. **Caching Strategy**:
   - Cache frequently accessed data (e.g., popular posts, user profiles) in Redis.
   - Implement cache invalidation to ensure data consistency when updates occur.

3. **Scalability**:
   - Use load balancers to distribute traffic across multiple backend servers.
   - Scale MongoDB and Redis horizontally to handle increasing data and traffic.

4. **Performance Optimization**:
   - Use pagination for fetching posts to reduce load on the database.
   - Optimize database queries and indexes for faster data retrieval.

5. **Real-Time Updates**:
   - Implement WebSockets or Server-Sent Events (SSE) for real-time notifications (e.g., new likes, comments).



---

### **Tech Stack**
- **Frontend**: Vue.js (web), React Native (mobile).
- **Backend**: Go with Gin (API server), Node.js with Express.js (real-time features).
- **Database**: MongoDB (primary database), Redis (caching).
- **Deployment**: Docker, Kubernetes, AWS/GCP for cloud hosting.

---

![socialMedia-benito](https://github.com/user-attachments/assets/4d89e172-f716-4de8-8eba-97b4bca721fa)

Explanation: 3 regions used to ensure 99.999% availability and to be fault tolerant

Cloud load balancer used to spread load across availability zones
Web tier and application tier for frontend and backend
Compute engine used for web and app servers
Cloud memorystore used for database - Memorystore is a fully-managed database service that provides a managed version of two popular open source caching solutions: Redis and Memcached


This architecture ensures **scalability**, **performance**, and **maintainability** for social media application. 
