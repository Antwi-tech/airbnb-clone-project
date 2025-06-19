# Internship Booking Platform
This is a full-stack **Internship Booking Platform** designed to connect **junior high schools** with **companies** offering short-term internship opportunities. Companies can list at least 2 weeks of availability, and schools can book internship slots for their students, either as part of the academic curriculum or for exposure to real-world experiences.The platform offers a smooth, Airbnb-style booking experience tailored specifically for internships. Schools manage students and bookings, while companies manage internship offers and availability.

![Airbnd](image.png)

## 🎯 Project Goals
- Provide a centralized system to connect schools with companies.
- Enable booking of internship slots with real-time availability.
- Empower students through early exposure to professional environments.
- Build and deploy a scalable, production-ready full-stack application.


## 🔑 Features Implemented
- 🔐 User authentication for schools and companies
- 🏢 Internship listings with duration and details
- 📅 Real-time booking system
- 🧑‍🏫 School dashboard for managing students and bookings
- 🧑‍💼 Company dashboard for managing availability
- 📎 Document upload (e.g. internship letters)
- 💬 Feedback and review system
- 📱 Fully responsive design


## Team Roles
**Backend Developer:** Engineers the product logic and algorithms that connects the systems together. Controls the server-side logic and maintains API's that connects to components of the application.

**Frontend Developer:** Engineers the interface the user interacts with. Ensures that the designs from the UI/UX team is implemented in code.

**Database Administrator:** Manages the database to ensure data integrity ,performance and security.Ensures that database queries are optimized.

**Business Analyst:** This individual performs the tasks of understanding customer business process and translates their needs into requirements, they analyze customer feedback in order to align customer's vision with development.

**Product Owners:** He/She enusres customer satisfaction in terms of making the customer product a success. They plan the product backlog to ensure that the vision of the customer is met.It is not however technical unlike the BA.

**Project Manager:** Ensures the timely delivery of product and make sure that expenditure is within budget. Plans activities, distributes roles and updates status of the team in relation to meeting timelines.

**UI/UX Designer:** Prepares a design that best suites the product vision and user journeys to explain interactivity between the user and the screen. Focuses on enhancing experience over time.

**Software Architects:** Designs the structure of overall system architecture. Puts in place what tools will be needed to build a product solution and sets up code quality standards and reviews.

**Quality Assurance Engineers:** Ensures that application matches requirements and sees the functional and non-functional defects. Evaluates what the application should do and how the application should do it, to fufil this, QA tests are cnducted.

**Test Automation Engineers:** Fufils the tasks of writing and maintainig a series of repetitive tasks through building a tests scripts that can carry out these tasks in without human involvment.

**DevOps Engineers:** Facilates cooperation between the developement and automation teams and builds continous integration and continous delivery pipelines to ensure faster devlivery of software. Manages infrastructure and monitors logging and cloud services.

## Technology Stack
#### Frontend:
**React.js:** It is an open source Javascript library used to build responsive user interfaces on UI components.

**Tailwind CSS (or Bootstrap):** A utility first CSS framework that allows developers to rapidly build custome interfacesdirectly within HTML.

**React Router:** Used to handle client-side routing navigation in react application.

**Axios / Fetch API:** Used to make HTTP requests to backend services from the frontend.

#### Backend:
**Node.js:** A javascript runtime environment that allows users to write server side logic using javascript

**Express.js:** A minimal and flexible Node.js framework used to build Restful API and handle HTTP requests

**MongoDB:** A NoSQL database used for stroing unstructured or semi-structured data as JSON-like documents

**JWT for authentication:** Used to verify the identity of a user and their permissions for authentication and authorization

#### DevOps:
**Docker:** A containerization tool that packages the ap and its dependencies to ensure consistency across environments.

**Kubernetes:** An orchestration tool used to automate deployment, sclaing and management of containerized applications.

**GitHub Actions:** A CI/CD tool that automates testing, building and deployment of code from GitHub.

**Amazon Web Services:** A cloud platform used to deploy services 

#### Testing:
**Jest:** A testing framework for javascript, commonly used to test frontend and backend logic.

**Cypress:** An end to end testing tool that tests how users interact with the application.

**Postman:** An API testing tool that allows developers anf QA to tests HTTP requests and backend API

**Selenium:** A browser automation tool for testing web applications across different browsers

#### Monitoring:
**Prometheus:** A monitoring system that collects and stores metrics from applications and infrastructure.

**Grafana:** A visaulisation tool used to display monitoring data from prometheus or sources in real time dashbaords.


## 🧱 Database Structure

This system uses a relational structure between entities to model real-world relationships between schools, companies, and internship processes.

### **`users`**
Stores profile information for both **schools** and **companies**.

- A user can be a **school** or a **company**
- A **company user** can:
  - Create multiple `internship_listings`
  - Receive multiple `bookings`
  - Upload `documents`
  - Receive `feedback` from schools
- A **school user** can:
  - Book multiple `internship_listings`
  - Submit `feedback`
  - Upload `documents` (e.g. approval letters)
  - View booking history


### **`internship_listings`**
Represents internships posted by companies.

- Each listing is **created by one company user**
- A listing:
  - Belongs to **one company**
  - Can have **multiple bookings**
  - Can receive **multiple feedback entries**
  - Can have **multiple attached documents**
- Includes:
  - Title, description, duration, available dates, location, skills required


### **`bookings`**
Represents a booking made by a school for an internship listing.

- Each booking:
  - Is **made by one school user**
  - Is linked to **one internship_listing**
  - Has a status: `pending`, `approved`, `rejected`, or `completed`
  - Can be associated with **one or more documents** (e.g. approval letters)
  - Can trigger a **feedback entry** upon completion


### **`feedback`**
Stores reviews and ratings from schools or companies.

- Each feedback:
  - Is written by **one user** (school or company)
  - Is related to **one internship_listing** or **booking**
  - Includes rating, comments, date
  - Optional (not required for all bookings)


### **`documents`**
Stores uploaded files like approval letters or internship agreements.

- Each document:
  - Is uploaded by **one user**
  - Can be associated with:
    - An **internship_listing**
    - A **booking**
  - Includes metadata (type, upload date, file path)

### 🔁 Summary of Relationships

| Entity                | Related To                          | Type of Relationship        |
|-----------------------|-------------------------------------|-----------------------------|
| `users`               | `internship_listings`               | 1:N (Company → Listings)    |
| `users`               | `bookings`                          | 1:N (School → Bookings)     |
| `users`               | `feedback`                          | 1:N (User → Feedback)       |
| `users`               | `documents`                         | 1:N (User → Documents)      |
| `internship_listings` | `bookings`                          | 1:N                         |
| `internship_listings` | `feedback`                          | 1:N                         |
| `internship_listings` | `documents`                         | 1:N                         |
| `bookings`            | `feedback`                          | 1:1 (optional)              |
| `bookings`            | `documents`                         | 1:N                         |



## 📊 Feature Breakdown

| Feature | Description |
|---------|-------------|
| 🙍🏽‍♂️ **User Management** | Sign up/login for companies & schools |
| 🏢 **Internship Listings** | Companies can add/update/delete listings |
| 📅 **Booking System** | Schools book available internship slots |
| 📤 **Document Upload** | Upload and view internship letters or confirmations |
| 🔍 **Search & Filters** | Browse listings by location, type, duration |
| ✍🏽 **Feedback System** | Leave or view feedback post-internship |
| 📱 **Responsive Design** | Works seamlessly on desktop and mobile |



## 🔐 API Security
To ensure that our backend APIs are protected from unauthorized access and malicious attacks, the following security measures will be implemented:

1. **Authentication**
- We will use **JWT (JSON Web Tokens)** to authenticate users.
- Only users with valid login credentials will be issued a token, which must be included in all protected API requests.
- **Why it’s important:** Prevents unauthorized users from accessing protected resources like user profiles, bookings, or property management.

2. **Authorization**
- Role-based access control (RBAC) will be enforced (e.g., distinguishing between guests and hosts).
- Certain endpoints (like creating a property) will only be accessible to authenticated hosts.
- **Why it’s important:** Ensures users only perform actions they’re permitted to (e.g., users can’t delete other people’s bookings).

3. **Rate Limiting**
- Implement rate limiting using tools like **Express Rate Limit** to control how many requests a client can make in a set time.
- This helps prevent abuse (e.g., brute force login attempts or DDoS attacks).
- **Why it’s important:** Protects server resources and improves stability and response time for legitimate users.

4. **Input Validation and Sanitization**
- Use libraries like **express-validator** to validate incoming requests.
- Prevent injection attacks (e.g., SQL injection, NoSQL injection, or XSS).
- **Why it’s important:** Ensures data integrity and protects the backend from malicious payloads.

5. **HTTPS**
- All API requests will be made over HTTPS to ensure secure data transmission.
- **Why it’s important:** Protects user credentials, personal data, and payment information from being intercepted during transmission.


## 🚀 CI/CD Pipeline
**CI/CD** stands for **Continuous Integration** and **Continuous Deployment/Delivery**. It is a set of practices and tools that automate the process of testing, building, and deploying applications. 

- **Continuous Integration (CI):** Automatically tests and integrates code changes as they are pushed to the repository.
- **Continuous Deployment/Delivery (CD):** Automatically deploys those tested changes to a staging or production environment.

### Why CI/CD is Important?
- 🛠️ **Faster Development:** Automates repetitive tasks like testing and deployment.
- ✅ **Higher Quality:** Ensures that new code does not break existing functionality through automated tests.
- 🔄 **Consistency:** Reduces human error by automating builds and deployments.
- 🚀 **Faster Releases:** Speeds up the time between coding and production deployment.

### Tools We Can Use
- **GitHub Actions:** Automate workflows for testing and deploying on every push or pull request.
- **Docker:** Containerize the application to ensure consistent environments across development, testing, and production.
- **Jest / Mocha:** For unit and integration testing in the CI phase.
- **Heroku / AWS / Vercel:** For automatic deployments once code passes all tests.
