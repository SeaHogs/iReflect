# PM-Tracker
A web app to track project milestones

## LightRAG environment configuration

The project now vendors the upstream LightRAG `.env` template so every service
reads from the same configuration file. The root `.env` includes defaults for
the server host/port, query limits, and model bindings. Update the OpenAI
credentials before running Docker Compose:

```dotenv
# Provide your OpenAI key once; docker-compose will forward it to both
# OPENAI_API_KEY and LLM_BINDING_API_KEY inside the LightRAG container so the
# service never falls back to a hard-coded credential.
LIGHTRAG_OPENAI_API_KEY=sk-...
```

Because the container receives both `OPENAI_API_KEY` and `LLM_BINDING_API_KEY`,
it will no longer attempt to authenticate with the placeholder credential that
ships with the upstream image.
