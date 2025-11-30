# AI Digital Twin

Um aplicativo de chat com IA que cria um "Digital Twin" personalizado usando OpenAI GPT-4o-mini. O projeto consiste em um backend FastAPI (Python) e um frontend Next.js (React/TypeScript).

## 🚀 Tecnologias

- **Backend**: FastAPI, Python 3.12+, OpenAI API
- **Frontend**: Next.js 16, React 19, TypeScript, Tailwind CSS
- **Gerenciador de Pacotes**: UV (Python)

## 📋 Pré-requisitos

- Python 3.12 ou superior
- Node.js 18+ e npm
- [UV](https://github.com/astral-sh/uv) instalado
- Chave de API da OpenAI

## 🛠️ Instalação

### 1. Instalar UV

Se você ainda não tem o UV instalado:

```bash
# Linux/macOS
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows (PowerShell)
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Ou via pip:
```bash
pip install uv
```

### 2. Configurar o Backend

```bash
cd backend

# Criar ambiente virtual e instalar dependências com UV
uv venv
source .venv/bin/activate  # No Windows: .venv\Scripts\activate

# Instalar dependências
uv pip install -e .

# Ou usar uv sync (se tiver uv.lock)
uv sync
```

### 3. Configurar Variáveis de Ambiente

Crie um arquivo `.env` na pasta `backend/`:

```bash
cd backend
touch .env
```

Adicione sua chave da OpenAI:

```env
OPENAI_API_KEY=sua_chave_aqui
CORS_ORIGINS=http://localhost:3000
```

### 4. Configurar o Frontend

```bash
cd frontend

# Instalar dependências
npm install
```

## 🎯 Como Usar

### Iniciar o Backend

```bash
cd backend
source .venv/bin/activate  # No Windows: .venv\Scripts\activate

# Executar o servidor
python server.py

# Ou usando uvicorn diretamente
uvicorn server:app --reload --host 0.0.0.0 --port 8000
```

O backend estará rodando em `http://localhost:8000`

### Iniciar o Frontend

Em outro terminal:

```bash
cd frontend
npm run dev
```

O frontend estará rodando em `http://localhost:3000`

## 📁 Estrutura do Projeto

```
twin/
├── backend/
│   ├── server.py          # Servidor FastAPI
│   ├── pyproject.toml     # Configuração do projeto Python
│   ├── me.txt             # Personalidade do Digital Twin
│   └── .env               # Variáveis de ambiente (não versionado)
├── frontend/
│   ├── app/               # Páginas Next.js
│   ├── components/        # Componentes React
│   └── package.json       # Dependências Node.js
└── memory/                # Arquivos de conversas salvas (não versionado)
```

## 🔧 Comandos Úteis com UV

### Gerenciar Dependências

```bash
# Adicionar uma nova dependência
uv add nome-do-pacote

# Adicionar dependência de desenvolvimento
uv add --dev nome-do-pacote

# Remover dependência
uv remove nome-do-pacote

# Atualizar todas as dependências
uv lock --upgrade

# Sincronizar ambiente com uv.lock
uv sync
```

### Executar Scripts

```bash
# Executar um script Python no ambiente virtual
uv run python script.py

# Executar comando diretamente
uv run uvicorn server:app --reload
```

## 🧠 Personalização

Para personalizar o comportamento do Digital Twin, edite o arquivo `backend/me.txt` com as características desejadas.

## 📝 API Endpoints

- `GET /` - Mensagem de boas-vindas
- `GET /health` - Health check
- `POST /chat` - Enviar mensagem e receber resposta
  ```json
  {
    "message": "Sua mensagem aqui",
    "session_id": "opcional-session-id"
  }
  ```
- `GET /sessions` - Listar todas as sessões salvas

## 🔒 Segurança

- Nunca commite arquivos `.env` ou chaves de API
- As conversas são salvas localmente na pasta `memory/`
- Configure `CORS_ORIGINS` adequadamente para produção

## 📄 Licença

Este projeto é parte de um curso sobre AI in Production.

## 🤝 Contribuindo

Este é um projeto educacional. Sinta-se à vontade para experimentar e modificar!

