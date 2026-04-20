┌─────────────────────────────────────────────────────────────────────────────────┐
│                          EXTERNAL CHANNELS (Multi-Source)                       │
│                                                                                 │
│        [LINE]   [Messenger]   [TikTok]   [Phone]   [Website]   [Email]          │
│          │          │            │         │         │           │              │
└──────────┼──────────┼────────────┼─────────┼─────────┼───────────┼──────────────┘
           │          │            │         │         │           │
           └──────────┴────────────┴─────────┴─────────┴───────────┘
                                   │
                        ┌──────────▼──────────┐
                        │   n8n Workflow      │
                        │   Engine (Event     │
                        │   Orchestrator)     │
                        └──────┬───────┬──────┘
                               │       │
                   ┌───────────┘       └───────────┐
                   │                               │
        ┌──────────▼────────────┐    ┌────────────▼──────────┐
        │   Chatbot Service     │    │   FastAPI Server      │
        │   (Rule-Based Q&A)    │    │   (Business Logic)    │
        └──────────┬────────────┘    └────────────┬──────────┘
                   │                               │
                   │        ┌──────────────────────┘
                   │        │
        ┌──────────▼────────▼──────────────────┐
        │     Data Validation & Processing     │
        └──────────┬───────────────────────────┘
                   │
        ┌──────────┴────────────────────────────┐
        │                                       │
        │    PRIMARY DATA LAYER (PostgreSQL)    │
        │                                       │
        │  • Customers (Profile, Contact)       │
        │  • Rooms (Type, Price, Status)        │
        │  • Bookings (Reservation Data)        │
        │  • Payments (Transaction Records)     │
        │  • Promotions (Offers, Validity)      │
        │  • Chat History (Conversation Logs)   │
        │  • Analytics (Behavioral Data)        │
        │                                       │
        └───────────────────────────────────────┘
                   ▲                   │`
                   │                   │
        ┌──────────┴────────────┐      │
        │     REDIS Cache       │      │
        │ (Session, Queue, TTL) │      │
        └───────────────────────┘      │
                                       │
                        ┌──────────────▼──────────────┐
                        │   Analytics Engine          │
                        │   (Reporting, Insights)     │
                        └─────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────────┐
│                        FUTURE: Home Automation Layer                            │
│                                                                                 │
│  [Sensors] ──MQTT──> [Mosquitto Broker] ──> [Home Assistant] ──> [LINE Alert]   │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘