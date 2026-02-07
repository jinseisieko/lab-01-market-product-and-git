## Product Choice

- Product name:  Wildberries
- Link to the product's website: www.wildberries.ru
- Short description of the product: Wildberries is an international online store for clothing, footwear, electronics, children's goods, household goods and other goods. In addition to Russia, the online store operates in Belarus, Kazakhstan, Kyrgyzstan and Armenia.

## Main components
![Wildberies diagram](../docs/diagrams/out/wildberries/architecture-component/Component%20Diagram.svg)
[Wildberies diagram](../docs/diagrams/src/wildberries/architecture-component.puml)

1. Mobile App (iOS/Android)
    This is the client application users install on smartphones to access Telegram’s features (messaging, calls, media sharing). It communicates with Telegram’s backend via the MTProto protocol for secure, real-time interactions.  
2. MTProto Protocol
    Telegram’s custom encryption protocol that secures data transmission between clients (mobile, desktop, web) and servers. It ensures end-to-end encryption for messages and other sensitive data during transit.  
3. MTProto Gateway (DC Entry)
    Acts as the entry point for client connections in the Connection Layer. It routes incoming requests from clients (using MTProto) to the appropriate backend services, managing connection lifecycle and load distribution.  
4. Message Handling Service
    A core service responsible for processing, queuing, and delivering messages across the Telegram ecosystem. It ensures reliable message transmission, handles message storage (temporarily), and coordinates delivery to recipients.  
5. State Cache (Redis)
    Uses Redis to cache frequently accessed data (e.g., user sessions, active chats) in the Data Layer. This reduces latency for read-heavy operations by serving cached data instead of querying primary databases, improving overall system performance.

## Data flow

![Wildberies diagram](../docs/diagrams/out/wildberries/architecture-sequence/Sequence%20Diagram.svg)
[Wildberies diagram](../docs/diagrams/src/wildberries/architecture-sequence.puml)

Payment Callback & Finalization

What happens:
After the user completes payment in the bank’s 3DS interface, the bank sends a webhook (callback) to Wildberries’ gateway. The system then validates the payment, updates the order status to PAID, and publishes an event to Kafka to decouple the payment confirmation from warehouse processing—ensuring resilience and scalability.

## Deployment

![Wildberies diagram](../docs/diagrams/out/wildberries/architecture-deployment/Deployment%20Diagram.svg)
[Wildberies diagram](../docs/diagrams/src/wildberries/architecture-deployment.puml)

Client-side components like the Customer Mobile App, Partner App, and Web Browser run on user devices (smartphones, computers), while enterprise hardware (e.g., warehouse terminals) operates on-premises. The core infrastructure—including gateways (Storefront, Partner, Internal/Ops), microservices (E-Commerce, Logistics, Support pods), and data layers (Redis, Elasticsearch, Kafka, PostgreSQL)—is deployed in Wildberries’ primary data center using Kubernetes (K8s) for orchestration. External dependencies like payment providers, logistics partners, and notification services (SMS/push) reside outside this infrastructure, integrated via APIs.

## Assumptions
- I assumed the microservices (Cart, OMS, Payment, Inventory) run in a Kubernetes cluster within a centralized data center, as this is a common pattern for scalable e-commerce platforms.
- I assumed the Inventory Service uses hard reservation (immediate stock decrement) rather than soft reservation (tentative hold) during checkout. 

## Open questions
- Do the Kafka Event Bus servers in Wildberries' cluster have a secret coffee break schedule to avoid 'event exhaustion'?
- Does the Redis cache in Wildberries’ Data Layer have a 'please don’t evict my cart items' VIP queue for users who add 100+ items to cart?

