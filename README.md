# Awesome-Webhooks-Event-Notification-System

# Awesome Webhooks & Event Notification System

> A curated list of top Webhooks and Event Notification System platforms — both SaaS/Hosted commercial solutions and open-source alternatives for reliable webhook delivery, event routing, and local debugging.  
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Svix](#svix)
  - [Hookdeck](#hookdeck)
  - [Zapier Webhooks](#zapier-webhooks)
  - [Make Webhooks](#make-webhooks)
  - [Pipedream](#pipedream)
  - [Courier](#courier)
  - [Webhook.site](#webhooksite)
  - [RequestBin](#requestbin)
- [Open-Source Software](#-open-source-software)
  - [Outpost (Hookdeck)](#outpost-hookdeck)
  - [Convoy](#convoy)
  - [WebhookX](#webhookx)
  - [Webhook Tester (tarampampam)](#webhook-tester-tarampampam)
  - [fasthook](#fasthook)
  - [Hook0](#hook0)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Webhook and Event Notification platforms. These are not open-source but are included as reference points for feature comparison.

### Svix
**Type:** Webhooks-as-a-service platform  
Svix is the leading commercial webhooks platform, offering a complete API for sending webhooks with built-in deliverability, retries, security (HMAC signing), and a white-label receiver portal [citation:4][citation:8]. The platform handles endpoint management, event type catalogs with schemas, filtering, transformations, and observability. Pricing tiers include a free tier for small volumes, with SLAs scaling from 99.9% to 99.999% on Enterprise [citation:8]. The core server is also open-source under MIT, making it a rare example of a commercial platform with a genuinely open-source core [citation:4].  
**Best for:** SaaS companies wanting to add production-grade webhooks to their product without building delivery infrastructure from scratch.

### Hookdeck
**Type:** Event gateway with webhook proxy and queue  
Hookdeck provides a webhook proxy and durable message queue that sits between providers and your application, guaranteeing ingestion even during downtime or traffic spikes [citation:6]. It eliminates the need for your own message queue for webhook processing — your handler just does business logic and returns a status code. Features include automatic retries, replay, rate limiting, filtering, transformations, and observability. The CLI (`hookdeck listen`) provides free, permanent event URLs for local development without ngrok [citation:13].  
**Best for:** Teams wanting to offload webhook reliability concerns (queueing, retries, replay) to a managed gateway.

### Zapier Webhooks
**Type:** Webhook triggers and actions within automation  
Zapier provides "Webhooks by Zapier" as a built-in app with triggers (Catch Hook, Catch Raw Hook) and actions (POST, GET, PUT). Commonly used to connect webhook-emitting services to 7,000+ apps without code. Lacks dedicated webhook infrastructure features like retries, signing, or observability — it is a lightweight glue layer.

### Make Webhooks
**Type:** Webhook modules within visual automation  
Make provides webhook modules (Custom Webhook, Webhook Response) within its visual scenario builder. Supports instant triggers via webhooks, with the ability to parse payloads, branch logic, and respond to the caller. More flexible than Zapier for webhook processing but still not a dedicated webhook delivery platform.

### Pipedream
**Type:** Developer-focused event source platform  
Pipedream provides HTTP webhook triggers and event sources as part of its workflow automation platform. Offers a code-first approach with Node.js/Python steps, built-in authentication handling, and event history. Suited for developers wanting programmatic control over webhook processing.

### Courier
**Type:** Notification infrastructure with webhook delivery  
Courier focuses on multi-channel notifications (email, SMS, push, chat) and includes webhook as a delivery channel. Provides templating, routing, and delivery tracking across channels. While not a pure webhook platform, it handles outbound webhook notifications as part of a broader notification orchestration system.

### Webhook.site
**Type:** Instant webhook testing and inspection  
Webhook.site generates a unique URL instantly for inspecting incoming HTTP requests and webhooks. Provides a web UI showing headers, body, query parameters, and method. A free, browser-based tool for quick debugging without local setup. Limited persistence and no production delivery features.

### RequestBin
**Type:** Request inspection and debugging  
RequestBin (now part of Pipedream) creates a unique endpoint for collecting and inspecting HTTP requests. Similar to Webhook.site, it is focused on debugging rather than production delivery. Useful for seeing exactly what a provider is sending.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Webhook and Event Notification tools. All listed projects offer source code you can deploy on your own infrastructure.

### Outpost (Hookdeck)
**Stack:** Go | **License:** Apache-2.0  
An open-source outbound webhooks and event destinations infrastructure built by Hookdeck [citation:2]. Supports webhooks, Hookdeck Event Gateway, Amazon EventBridge, AWS SQS, AWS S3, GCP Pub/Sub, RabbitMQ, and Kafka as destination types. Features include topic-based subscriptions, publish via API or queue, at-least-once delivery guarantee, event fanout, automatic and manual retries, multi-tenant support, a user portal for customers, delivery failure alerts, and OpenTelemetry integration. Ships with Go, Python, and TypeScript SDKs plus an MCP server [citation:2]. Runtime dependencies are minimal (Redis, PostgreSQL, and an optional message queue).  
**Best for:** Platforms wanting to add production-grade outbound webhooks to their product without building delivery, retry, and tenant management from scratch.

### Convoy
**Stack:** Go | **License:** Open Source (per project)  
An open-source high-performance webhooks gateway for managing millions of webhooks end-to-end [citation:5]. Supports both **incoming** projects (receive webhooks from providers with a unique URL per provider) and **outgoing** projects (publish events from your systems to your customers via API) [citation:12]. Features include retries, filtering, transformations, portal links, and observability. Positioned as a complete webhook proxy that can both ingest from providers and publish to customers.  
**Best for:** Teams needing a unified gateway for both receiving provider webhooks and sending outbound webhooks to customers.

### WebhookX
**Stack:** Go | **License:** Open Source (production license required for commercial use)  
An open-source webhook gateway for receiving, validating, transforming, and delivering events at scale [citation:9]. Features include an Admin API, reliable delivery with automatic retries, fanout to multiple endpoints by event type, rate limiting, declarative configuration (GitOps-oriented), plugins (WASM transforms, signature verification, event validation), and OpenTelemetry observability. Requires PostgreSQL and Redis. **Note:** Multi-tenancy and secret management require a license; free production licenses are available for eligible non-commercial use [citation:9].  
**Best for:** Teams wanting a Go-based, plugin-extensible webhook gateway with declarative configuration and GitOps workflows.

### Webhook Tester (tarampampam)
**Stack:** Go / React | **License:** Open Source (per repository)  
A free, self-hosted alternative to webhook.site and RequestBin [citation:7]. Generates unique URLs for capturing and inspecting HTTP requests. Features include customizable response codes/headers/body, WebSocket real-time UI updates, optional ngrok tunneling for exposing local instances to the internet, three storage drivers (memory, Redis, filesystem), and a lightweight Docker image. Supports pre-defined static webhook URLs via UUID prefixes with `--auto-create-sessions` [citation:7].  
**Best for:** Developers and teams wanting a self-hosted, privacy-respecting webhook inspector for debugging and testing.

### fasthook
**Stack:** Python / FastAPI | **License:** Open Source (per PyPI)  
A local webhook receiver for testing and development with no ngrok, no cloud dashboard, and no signup [citation:3]. Version 2.0 adds production-ready features: mock server mode with scripted responses, event replay with adjustable speed, forwarding with exponential backoff retries, connection pooling, structured logging, and graceful shutdown. Saves events as newline-delimited JSON for use with `jq` or pandas. Installable via `pip install fasthook` [citation:3].  
**Best for:** Developers wanting a simple, scriptable local webhook catcher that can also mock responses and replay events for testing.

### Hook0
**Stack:** (Check repository) | **License:** Open Source (per project)  
An open-source webhooks-as-a-service platform with a dashboard, receiver portal (basic branding), event types, and subscriptions by event type [citation:8]. Supports custom headers, and offers EU region data residency. Metrics API available; OpenTelemetry is not supported. Retention tiers range from 7 to 30 days. SLA of 99.9% on paid tiers.  
**Best for:** European teams wanting a self-hostable webhooks platform with EU data residency and a basic customer portal.

---

## 📊 Comparison at a Glance

| Software | License | Type | Inbound | Outbound | Self-Hosted | Best For |
|----------|---------|------|---------|----------|-------------|----------|
| **Svix** | Proprietary (MIT core) | Webhooks-as-a-service | ❌ | ✅ | ✅ (core) | Product webhooks with SLA |
| **Hookdeck** | Proprietary | Event gateway | ✅ | ✅ | ❌ | Managed webhook reliability |
| **Zapier Webhooks** | Proprietary | Automation glue | ✅ | ✅ | ❌ | No-code app connections |
| **Make Webhooks** | Proprietary | Automation glue | ✅ | ✅ | ❌ | Visual webhook scenarios |
| **Pipedream** | Proprietary | Developer event source | ✅ | ✅ | ❌ | Code-first webhook processing |
| **Webhook.site** | Proprietary | Testing/inspection | ✅ | ❌ | ❌ | Quick browser-based debugging |
| **Outpost** | Apache-2.0 | Outbound webhook infra | ❌ | ✅ | ✅ | Product outbound webhooks |
| **Convoy** | Open Source | Webhook gateway | ✅ | ✅ | ✅ | Unified inbound + outbound |
| **WebhookX** | Open Source (licensed) | Webhook gateway | ✅ | ✅ | ✅ | Plugin-extensible gateway |
| **Webhook Tester** | Open Source | Testing/inspection | ✅ | ❌ | ✅ | Self-hosted inspector |
| **fasthook** | Open Source | Local receiver | ✅ | ❌ | ✅ (local) | Dev testing + replay |
| **Hook0** | Open Source | Webhooks platform | ❌ | ✅ | ✅ | EU self-hosted webhooks |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Webhook or Event Notification tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
