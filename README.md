# 🌐 MCP Streamable HTTP — Comunicação em Tempo Real com Model Context Protocol

Projeto que implementa um servidor/cliente baseado em **MCP (Model Context Protocol)** utilizando **HTTP streamável**, permitindo comunicação eficiente, contínua e em tempo real com modelos de linguagem (LLMs).

O objetivo é demonstrar como construir sistemas de IA que suportam **streaming de respostas**, melhorando performance e experiência do usuário em aplicações interativas.

---

## 🧠 Conceitos Abordados

- 🔌 Model Context Protocol (MCP)  
- 🌊 Streaming de respostas via HTTP  
- ⚡ Comunicação em tempo real com LLMs  
- 🧠 Gerenciamento de contexto  
- 🔄 Integração com múltiplos provedores  

---

## 🚀 Tecnologias Utilizadas

### 🔙 Backend
- Python 3.10+ *(ou Node.js dependendo da implementação)*  
- FastAPI / Express  
- Uvicorn / Node runtime  

### 🌊 Streaming
- HTTP Streaming (chunked transfer)  
- Server-Sent Events (SSE) *(se aplicável)*  

### 🧠 IA
- OpenAI API  
- Hugging Face *(opcional)*  

### ⚙️ Infra
- dotenv  
- Requests / HTTPX / Axios  

---

## ⚙️ Como Rodar o Projeto Localmente

### 1️⃣ Clonar o Repositório

```bash
git clone <url-do-repositorio>
cd mcp_streamable_http-main
```
2️⃣ Criar Ambiente
```
python -m venv venv
source venv/bin/activate
```
Windows:
```
venv\Scripts\activate
```
3️⃣ Instalar Dependências
```
pip install -r requirements.txt
```
4️⃣ Configurar Variáveis de Ambiente

Crie um .env:
```
OPENAI_API_KEY=your_api_key_here
MODEL_NAME=gpt-4
STREAM_MODE=true
```
5️⃣ Executar o Servidor
```
uvicorn app.main:app --reload
```

Ou:
```
python main.py
```
Servidor disponível em:
```
👉 http://localhost:8000
```

🌊 Como Funciona o Streaming

Ao invés de esperar a resposta completa do modelo, o sistema:

- Envia prompt ao modelo
- Recebe resposta em partes (tokens/chunks)
- Transmite ao cliente em tempo real
- Renderiza incrementalmente

📡 Endpoints Principais
🔹 Streaming de Resposta
POST /stream

Body:

{
  "prompt": "Explique o que é streaming em IA"
}

Resposta:

Fluxo contínuo de texto (chunked response)
🔹 Chat com Streaming
POST /chat/stream
🔹 Health Check
GET /health

---

🧠 Arquitetura do Projeto
```
.
├── app/
│   ├── main.py
│   ├── routes/
│   ├── services/
│   ├── streaming/
│   └── context/
├── config/
├── requirements.txt
├── .env
└── README.md
```

---

🧠 Decisões Técnicas

- Uso de HTTP streaming para reduzir latência percebida
- Implementação compatível com MCP
- Separação de responsabilidades:
- streaming/ → lógica de stream
- services/ → integração com IA
- Arquitetura preparada para múltiplos provedores
- Configuração via .env

---

📦 Funcionalidades Implementadas

- 🌊 Streaming de respostas em tempo real
- 🔌 Integração com MCP
- 🧠 Gerenciamento de contexto
- ⚙️ API REST + streaming
- 🔄 Compatível com múltiplos modelos
- ⚡ Benefícios do Streaming
- ⏱️ Redução de latência percebida
- 🧠 Experiência mais natural (tipo ChatGPT)
- 📡 Melhor uso de rede
- 🔄 Feedback contínuo ao usuário
- 🐳 Docker
- docker build -t mcp-stream .
- docker run -p 8000:8000 mcp-stream

---

🚀 Deploy

- Cloud (Render / Railway / AWS)

Configurar:
```
uvicorn app.main:app --host 0.0.0.0 --port 8000
```
Variáveis:
```
OPENAI_API_KEY
MODEL_NAME
```

---

🔐 Segurança

- Não versionar .env
- Implementar rate limit
- Monitorar uso de tokens
- Autenticar endpoints em produção

---

📈 Possíveis Evoluções

- 🔄 WebSockets (tempo real avançado)
- 🧠 Memória persistente
- 🔍 RAG com embeddings
- 📊 Observabilidade (logs + métricas)
- ⚡ Cache de respostas
- 🤖 Integração com agentes (CrewAI / LangGraph)

---

🎯 Objetivo do Projeto

- Demonstrar streaming com LLMs
- Implementar MCP com HTTP
- Melhorar UX em aplicações com IA
- Servir como base para sistemas em tempo real

---

📚 Referências

- https://platform.openai.com/docs/api-reference/streaming
- https://developer.mozilla.org/en-US/docs/Web/API/Streams_API
- https://fastapi.tiangolo.com
---
