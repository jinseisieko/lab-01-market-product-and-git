## Components and roles

- **Mobile App (iOS/Android)**
  - Mobile Engineer (Kotlin/Swift)
  - QA Engineer (Mobile Testing)
  - UX/UI Designer
  - Product Manager
- **Storefront Gateway**
  - Backend Engineer (API Gateway)
  - DevOps Engineer
  - Security Engineer
  - SRE (Site Reliability Engineer)
- **Order Management Service (OMS)**
  - Backend Engineer (Java/Go)
  - QA Engineer (Integration Testing)
  - Database Administrator
- **Payment Service**
  - Backend Engineer
  - Security Engineer (PCI DSS compliance)
  - QA Engineer (Payment Flows)
- **Inventory Service**
  - Backend Engineer
  - Data Engineer
  - QA Engineer
- **Kafka Event Bus**
  - Platform Engineer
  - DevOps Engineer
  - SRE
- **State Cache (Redis)**
  - Backend Engineer
  - DevOps Engineer
  - SRE

## Roles and responsibilities

1. **Backend Engineer**
   - Develops and maintains microservices (OMS, Payment, Inventory)
   - Designs REST/gRPC APIs for client and service communication
   - Implements business logic for order processing, stock management, and payment flows
   - Optimizes database queries and ensures data consistency across services

2. **Mobile Engineer**
   - Builds and maintains iOS/Android applications using Kotlin/Swift
   - Integrates with backend APIs for product catalog, cart, and checkout flows
   - Implements offline capabilities and push notifications
   - Ensures app performance and compatibility across device models

3. **DevOps Engineer**
   - Manages Kubernetes clusters and container orchestration
   - Configures CI/CD pipelines for automated testing and deployment
   - Maintains infrastructure as code (Terraform/Ansible)
   - Implements monitoring, logging, and alerting systems (Prometheus, Grafana)

4. **Security Engineer**
   - Implements secure authentication and authorization (OAuth2, JWT)
   - Ensures PCI DSS compliance for payment data handling
   - Conducts security audits and vulnerability assessments
   - Designs DDoS protection and API rate limiting strategies

5. **SRE (Site Reliability Engineer)**
   - Defines and monitors SLOs/SLIs for service reliability
   - Manages incident response and post-mortem analysis
   - Automates operational tasks to reduce manual intervention
   - Plans capacity for traffic spikes (e.g., during sales events)

## Common skills across roles

- **Programming**: Java/Go (backend), Kotlin/Swift (mobile), Python (scripts)
- **Databases**: PostgreSQL (transactional data), Redis (caching), Elasticsearch (search)
- **Messaging**: Kafka for event-driven architecture and decoupling services
- **Cloud/Infra**: Kubernetes, Docker, AWS/GCP fundamentals
- **APIs**: REST, gRPC, OpenAPI specifications
- **Tools**: Git, Jira, Postman, Grafana, Kibana
- **Practices**: Agile/Scrum, test-driven development, documentation
- **Soft skills**: Cross-functional collaboration, clear communication, problem-solving under pressure