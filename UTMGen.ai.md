# Technical Documentation for UTMGen.ai

## Overview
UTMGen.ai is a web application designed to create, manage, and track UTM parameters in URLs. The application will provide features for generating UTM links, shortening them, tracking their performance, and generating detailed reports. The tech stack includes React.js for the frontend, Node.js for the backend, PostgreSQL for relational data, and MongoDB for non-relational data.

## Tech Stack
- **Frontend**: React.js
- **Backend**: Node.js
- **Database**: PostgreSQL, MongoDB
- **Authentication**: OAuth2 (Google), JWT
- **Hosting**: AWS/GCP/Azure (TBD)
- **CI/CD**: Jenkins/GitLab CI (TBD)

## Team Members
- **Backend Developer**: 1 full-time
- **Frontend Developers**: 2 full-time
- **Delivery Manager, DevOps, Senior Code Reviewer**: On ad hoc basis
- **UI/UX Designer**: Not applicable (using UTM.io's UX)

## Project Timeline
- **Total Duration**: 3 months
- **Sprints**: 6 sprints (2 weeks each)

---

Here’s a detailed **sprint-by-sprint plan** for the development of UTMGen.ai. Each sprint is **2 weeks long**, and the plan includes tasks, deliverables, and goals for each sprint.

---

## **Sprint 1: Authentication and User Management (Part 1)**

### **Goal**: Implement login, signup, and forgot password functionality.

#### **Tasks**:
1. **Backend**:
   - Set up Node.js server with Express.
   - Create PostgreSQL database and `users` table.
   - Implement JWT-based authentication.
   - Develop API endpoints:
     - `POST /api/auth/login`
     - `POST /api/auth/signup`
     - `POST /api/auth/forgot-password`
     - `POST /api/auth/reset-password`
   - Integrate email service (e.g., SendGrid) for password reset emails.

2. **Frontend**:
   - Create React components for:
     - Login page
     - Signup page
     - Forgot password page
   - Implement form validation for all pages.
   - Integrate API calls for login, signup, and forgot password.

3. **DevOps**:
   - Set up basic CI/CD pipeline for backend and frontend.
   - Deploy initial version of the app to a staging environment.

#### **Deliverables**:
- Functional login, signup, and forgot password flows.
- Email service for password reset.
- Basic CI/CD pipeline.

---

## **Sprint 2: Authentication and User Management (Part 2)**

### **Goal**: Implement Google login, user management, roles, and notifications.

#### **Tasks**:
1. **Backend**:
   - Integrate Google OAuth2 for login.
   - Create `roles` and `permissions` tables in PostgreSQL.
   - Develop API endpoints:
     - `GET /api/users` (Admin only)
     - `GET /api/users/:id`
     - `PUT /api/users/:id`
     - `DELETE /api/users/:id`
   - Implement notification system for key actions (e.g., account creation, password reset).

2. **Frontend**:
   - Create React components for:
     - Admin dashboard (user management)
     - Notification system (toast messages)
   - Integrate Google login button.
   - Implement role-based access control (e.g., Admin vs. User views).

3. **DevOps**:
   - Set up monitoring for the staging environment.
   - Ensure secure storage of secrets (e.g., JWT secret, Google OAuth credentials).

#### **Deliverables**:
- Google login integration.
- Admin dashboard for user management.
- Role-based access control.
- Notification system.

---

## **Sprint 3: UTM Link Builder**

### **Goal**: Build the UTM link generation feature.

#### **Tasks**:
1. **Backend**:
   - Create `utm_links` table in PostgreSQL.
   - Develop API endpoints:
     - `POST /api/utm/generate` (Generate UTM link)
   - Validate UTM parameters (source, medium, campaign, etc.).
   - Store generated UTM links in the database.

2. **Frontend**:
   - Create React components for:
     - UTM link builder form
     - Display generated UTM links
   - Implement input validation for UTM parameters.
   - Add copy-to-clipboard functionality for generated links.

3. **DevOps**:
   - Optimize database queries for UTM link generation.
   - Ensure scalability of the UTM link generation API.

#### **Deliverables**:
- Functional UTM link builder.
- Database storage for generated UTM links.
- Copy-to-clipboard functionality.

---

## **Sprint 4: UTM Link Shortener**

### **Goal**: Implement UTM link shortening and history tracking.

#### **Tasks**:
1. **Backend**:
   - Integrate a URL shortening service (e.g., Bitly API) or build a custom shortener.
   - Develop API endpoints:
     - `POST /api/utm/shorten` (Shorten UTM link)
   - Store shortened URLs in the `utm_links` table.
   - Add functionality to fetch and display a user’s UTM link history.

2. **Frontend**:
   - Create React components for:
     - Display shortened URLs
     - UTM link history
   - Add functionality to save and display history of generated links.

3. **DevOps**:
   - Ensure high availability of the URL shortening service.
   - Monitor API performance for UTM link shortening.

#### **Deliverables**:
- Functional UTM link shortener.
- History of generated links.
- Display of shortened URLs.

---

## **Sprint 5: UTM Campaign Tracking**

### **Goal**: Implement UTM link click tracking.

#### **Tasks**:
1. **Backend**:
   - Create `clicks` collection in MongoDB for tracking link clicks.
   - Develop API endpoints:
     - `POST /api/utm/track` (Track UTM link click)
     - `GET /api/utm/clicks` (Get click data for a UTM link)
   - Store click data (e.g., IP address, user agent, timestamp).

2. **Frontend**:
   - Create React components for:
     - UTM link tracking dashboard
   - Display click data for each UTM link.

3. **DevOps**:
   - Optimize MongoDB queries for click tracking.
   - Ensure scalability of the tracking system.

#### **Deliverables**:
- Functional UTM link tracking system.
- Dashboard to view click data.

---

## **Sprint 6: UTM Reporting Module**

### **Goal**: Implement reporting and visualization features.

#### **Tasks**:
1. **Backend**:
   - Develop API endpoints:
     - `GET /api/reports` (Generate UTM link performance report)
   - Aggregate click data for reporting (e.g., clicks by source, medium, campaign).
   - Add functionality to export reports as CSV/PDF.

2. **Frontend**:
   - Create React components for:
     - Reporting dashboard
     - Charts and graphs (e.g., using Chart.js or D3.js)
   - Implement export functionality for reports.

3. **DevOps**:
   - Optimize report generation for large datasets.
   - Ensure secure handling of exported reports.

#### **Deliverables**:
- Functional reporting dashboard.
- Charts and graphs for UTM link performance.
- Export functionality for reports.

---

## **Post-Development (Post-Sprint 6)**

### **Tasks**:
1. **Testing**:
   - Perform end-to-end testing using Cypress.
   - Conduct load testing for UTM link tracking and reporting features.

2. **Deployment**:
   - Deploy the final version of the app to production.
   - Set up monitoring and alerting for the production environment.

3. **Documentation**:
   - Write user documentation for the app.
   - Create a developer guide for future maintenance.

---

This sprint-by-sprint plan ensures a structured and phased approach to building UTMGen.ai. Each sprint has clear goals, tasks, and deliverables, making it easier to track progress and ensure timely delivery.

---

## Database Schema

### PostgreSQL (Relational Data)
1. **Users Table**:
   - `id` (UUID)
   - `email` (String)
   - `password` (String, hashed)
   - `role` (String: Admin/User)
   - `created_at` (Timestamp)
   - `updated_at` (Timestamp)

2. **UTM Links Table**:
   - `id` (UUID)
   - `user_id` (UUID, Foreign Key)
   - `original_url` (String)
   - `short_url` (String)
   - `utm_source` (String)
   - `utm_medium` (String)
   - `utm_campaign` (String)
   - `utm_term` (String, optional)
   - `utm_content` (String, optional)
   - `created_at` (Timestamp)

### MongoDB (Non-Relational Data)
1. **Clicks Collection**:
   - `link_id` (UUID, references UTM Links Table)
   - `timestamp` (Timestamp)
   - `ip_address` (String)
   - `user_agent` (String)
   - `referrer` (String, optional)

---

## API Endpoints

### Authentication
- `POST /api/auth/login` - User login.
- `POST /api/auth/signup` - User registration.
- `POST /api/auth/forgot-password` - Forgot password.
- `POST /api/auth/reset-password` - Reset password.
- `GET /api/auth/google` - Google OAuth2 login.

### User Management
- `GET /api/users` - Get all users (Admin only).
- `GET /api/users/:id` - Get user by ID.
- `PUT /api/users/:id` - Update user.
- `DELETE /api/users/:id` - Delete user.

### UTM Link Builder
- `POST /api/utm/generate` - Generate UTM link.
- `POST /api/utm/shorten` - Shorten UTM link.

### UTM Campaign Tracking
- `POST /api/utm/track` - Track UTM link click.
- `GET /api/utm/clicks` - Get click data for a UTM link.

### Reporting
- `GET /api/reports` - Generate UTM link performance report.

---

## Testing and Deployment
- **Testing**: Jest for unit testing, Cypress for end-to-end testing.
- **Deployment**: Dockerize the application for easy deployment. Use CI/CD pipelines for automated testing and deployment.

---

## Risks and Mitigation
1. **Risk**: Delays in third-party API integrations (e.g., Google OAuth, URL shortener).  
   **Mitigation**: Have fallback options or custom implementations.
2. **Risk**: Scalability issues with MongoDB for click tracking.  
   **Mitigation**: Optimize queries and use indexing.
3. **Risk**: UI/UX limitations due to cost-cutting.  
   **Mitigation**: Use open-source React component libraries (e.g., Material-UI).

---

This documentation provides a high-level overview of the project, sprint details, and technical requirements. Adjustments can be made based on team feedback and project progress.

