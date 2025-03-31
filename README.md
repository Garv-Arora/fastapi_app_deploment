
## 🌍 Overview
This project is a complete end-to-end industrial application built to calculate Economic Order Quantity (EOQ) and provide actionable inventory decisions. It showcases the integration of backend development, cloud hosting, DevOps automation, data persistence, user interface, monitoring, and security best practices.

---

## 💡 Use Case
**Industrial Engineering meets TechOps**: Minimize inventory cost by calculating EOQ using order cost, demand, and holding cost. This API-based solution is extendable, monitored, secure, and user-accessible.

---

## ⚖️ Technology Stack Breakdown

### 1. **FastAPI**
- Lightweight modern Python web framework.
- Handles all HTTP requests and business logic.
- Endpoints:
  - `/ping` for health check
  - `/eoq` for EOQ calculation

### 2. **Docker**
- Containerizes the FastAPI app for consistent development-to-deployment flow.
- Enables one-command app launch on any environment.

### 3. **AWS EC2**
- Cloud host for deploying the containerized application.
- Ubuntu-based virtual machine running Docker and FastAPI.
- Open ports 22 (SSH), 80 (HTTP).

### 4. **NGINX** (optional but production-recommended)
- Reverse proxy server for routing, logging, and SSL integration.
- Simplifies public access to internal services.

### 5. **PostgreSQL**
- Database for logging every EOQ request.
- Fields stored: order cost, demand, holding cost, result, timestamp.
- Accessed via SQLAlchemy ORM.

### 6. **SQLAlchemy**
- Object Relational Mapper (ORM) to connect FastAPI with PostgreSQL.
- Enables easy and safe DB operations.

### 7. **Streamlit**
- Lightweight frontend framework for quick UIs.
- Built a client-facing EOQ calculator UI that consumes the FastAPI backend.

### 8. **Prometheus**
- Metrics collector for monitoring API performance.
- Scrapes `/metrics` from FastAPI using `prometheus-fastapi-instrumentator`.

### 9. **Grafana**
- Dashboard tool to visualize Prometheus metrics.
- Displays request count, latency, error rates, etc.

### 10. **GitHub Actions (CI/CD)**
- Automates deployment pipeline.
- On every push to `main` branch:
  - Pulls code on EC2
  - Rebuilds Docker image
  - Restarts app container

### 11. **Certbot + Let’s Encrypt (SSL)**
- Provides HTTPS encryption to secure the application.
- Auto-renews SSL certificates.

### 12. **API Key Auth**
- Lightweight access control for endpoints.
- Requires `x-api-key` in headers to access any route.

### 13. **JWT (JSON Web Token) Auth**
- Future-ready token-based user authentication.
- Issues access tokens per user/session.
- Verifies token on each request.

### 14. **Logging**
- Every `/eoq` call logs input and output data.
- Saved to `app.log` for auditing, debugging.

---

## 📂 File & Directory Structure
```bash
inventory_api/
├── main.py              # FastAPI logic + auth + DB insertions
├── requirements.txt     # Python dependencies
├── Dockerfile           # Docker config
├── .github/workflows/   # GitHub Actions for CI/CD
├── app.log              # Request logs
├── ui.py                # Streamlit-based UI client
```

---

## ⚡ Workflow Summary

1. **Development**:
   - Build and test locally using Uvicorn
   - Streamlit UI developed and tested

2. **Containerization**:
   - Dockerfile wraps the app for consistent packaging

3. **Deployment**:
   - EC2 instance runs Dockerized app
   - Optionally uses NGINX as reverse proxy
   - SSL enabled via Certbot

4. **CI/CD**:
   - GitHub pushes trigger GitHub Actions workflow
   - SSH into EC2 and redeploys automatically

5. **Persistence**:
   - PostgreSQL logs all inputs and outputs

6. **Monitoring**:
   - Prometheus scrapes FastAPI metrics
   - Grafana visualizes them

7. **Security**:
   - API Key and JWT-based auth for endpoint protection

---

## 📊 Business Value
- Shows how a single engineer can build full product stack.
- Bridges industrial need (EOQ) with modern DevOps, automation, and cloud.
- Excellent for portfolios targeting tech-ops roles.

---

## 📖 Learning Outcome
- Real-world experience in backend development, API design
- Cloud infra management (AWS EC2, Docker)
- CI/CD pipeline creation
- Database operations and secure data handling
- Monitoring stack understanding (Prometheus + Grafana)
- UI creation with Streamlit for user testing/demo
- Token-based and key-based auth mechanisms

