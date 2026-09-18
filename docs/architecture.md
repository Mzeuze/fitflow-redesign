# FitFlow Reference Architecture

![FitFlow Reference Architecture](architecture.png)

The architecture is organized into five horizontal layers so responsibilities remain clear and independently scalable.

## 1. Experience Layer
- Android App: Jetpack Compose
- iOS App: SwiftUI
- Shared Mobile Core: Kotlin Multiplatform
- Web App: React + TypeScript

## 2. Access & Identity Layer
- AWS Cognito for authentication and user management
- API Gateway for request routing and throttling
- CDN / WAF for edge delivery and protection
- Rate limiting for abuse protection

## 3. Core Platform Services
Go-based services handle the main product logic:
- User & Profile Service
- Workout Planning Service
- Nutrition Service
- Social & Challenge Service
- Notification Service
- Integration Adapter Service

## 4. Intelligence & Event Layer
- Python + FastAPI AI service
- Recommendation engine
- Meal image analysis
- Event bus / asynchronous jobs
- WebSocket hub for live updates

## 5. Data & External Systems Layer
- PostgreSQL as the primary database
- Redis for caching and ephemeral state
- Object storage for meal images and other files
- Apple Health / Health Connect
- Payment gateway
- Email / push provider

## Key User Flows

### Personalized Workout Plan
User -> Workout Service -> AI Recommendation -> PostgreSQL -> Plan Returned

### Social Challenge Update
User -> Social Service -> Event Bus -> WebSocket Hub -> Connected Users

### Meal Logging
User -> Nutrition Service -> Object Storage -> AI Analysis -> Nutrition Record

## Cross-Cutting Concerns
- OAuth 2.0 / OpenID Connect security
- Audit logging
- Monitoring and alerting
- Privacy and consent controls
- Stateless horizontal scaling
