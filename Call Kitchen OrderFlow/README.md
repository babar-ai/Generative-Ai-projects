CALL KITCHEN ORDERFLOW PROJECT

Technical Architecture 

callkitchen/
├── README.md
├── requirements.txt
├── .env.example
├── .gitignore
├── setup.py
│
├── src/
│   ├── __init__.py
│   ├── main.py                 # Entry point
│   │
│   ├── agents/                 # All agent logic
│   │   ├── __init__.py
│   │   ├── base_agent.py      # Abstract base class
│   │   ├── order_agent.py     # Phase 1: Single agent
│   │   ├── orchestrator.py    # Phase 2: Multi-agent coordinator
│   │   └── specialized/       # Phase 2+: Specialized agents
│   │       ├── __init__.py
│   │       ├── validation_agent.py
│   │       ├── kitchen_agent.py
│   │       └── payment_agent.py
│   │
│   ├── core/                  # Core business logic
│   │   ├── __init__.py
│   │   ├── models.py          # Data models/schemas
│   │   ├── menu.py            # Menu operations
│   │   ├── order.py           # Order processing
│   │   └── pricing.py         # Price calculations
│   │
│   ├── integrations/          # External service integrations
│   │   ├── __init__.py
│   │   ├── kitchen_system.py  # Kitchen display/POS
│   │   ├── payment.py         # Payment processors
│   │   ├── voice/             # Phase 3: Voice services
│   │   │   ├── __init__.py
│   │   │   ├── stt.py         # Speech-to-text
│   │   │   ├── tts.py         # Text-to-speech
│   │   │   └── telephony.py   # Twilio integration
│   │   └── notifications.py   # SMS/Email services
│   │
│   ├── database/              # Data layer
│   │   ├── __init__.py
│   │   ├── connection.py      # DB connections
│   │   ├── repositories/      # Data access layer
│   │   │   ├── __init__.py
│   │   │   ├── menu_repo.py
│   │   │   ├── order_repo.py
│   │   │   └── customer_repo.py
│   │   └── migrations/        # DB schema changes
│   │
│   ├── api/                   # Phase 3+: REST API endpoints
│   │   ├── __init__.py
│   │   ├── app.py            # FastAPI app
│   │   ├── routes/
│   │   │   ├── __init__.py
│   │   │   ├── orders.py
│   │   │   ├── voice.py
│   │   │   └── webhook.py
│   │   └── middleware/       # Auth, logging, etc.
│   │
│   ├── utils/                # Utilities and helpers
│   │   ├── __init__.py
│   │   ├── config.py         # Configuration management
│   │   ├── logging.py        # Logging setup
│   │   ├── validators.py     # Input validation
│   │   └── exceptions.py     # Custom exceptions
│   │
│   └── interfaces/           # User interfaces
│       ├── __init__.py
│       ├── console.py        # Phase 1: Console interface
│       ├── web.py           # Phase 2+: Web interface
│       └── webhook_handler.py # Phase 3+: Twilio webhooks
│
├── data/                     # Static data files
│   ├── menu/
│   │   ├── items.json       # Phase 1: Simple menu
│   │   ├── categories.json
│   │   └── pricing.json
│   ├── prompts/             # Agent prompts and templates
│   │   ├── system_prompts.json
│   │   ├── order_templates.json
│   │   └── response_templates.json
│   └── sample_data/         # Test data
│       ├── sample_orders.json
│       └── test_conversations.json
│
├── tests/                   # All test files
│   ├── __init__.py
│   ├── conftest.py         # Test configuration
│   ├── unit/               # Unit tests
│   │   ├── __init__.py
│   │   ├── test_agents.py
│   │   ├── test_core.py
│   │   └── test_utils.py
│   ├── integration/        # Integration tests
│   │   ├── __init__.py
│   │   ├── test_voice_flow.py
│   │   └── test_order_flow.py
│   └── fixtures/           # Test data
│       ├── menu_fixtures.json
│       └── conversation_fixtures.json
│
├── config/                 # Configuration files
│   ├── development.yaml
│   ├── production.yaml
│   └── test.yaml
│
├── scripts/                # Utility scripts
│   ├── setup_db.py
│   ├── load_menu.py
│   └── test_conversation.py
│
├── docs/                   # Documentation
│   ├── api_docs.md
│   ├── deployment.md
│   └── architecture.md
│
└── docker/                 # Phase 4: Containerization
    ├── Dockerfile
    ├── docker-compose.yml
    └── docker-compose.prod.yml