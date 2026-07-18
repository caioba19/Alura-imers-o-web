# Análise do Projeto: Imersão Alura 07/2026 — Álbum de Figurinhas Virtual

> Atualizado em: 17/07/2026

---

## Visão Geral

Este é um projeto da **Imersão Alura** que implementa um **álbum de figurinhas virtual interativo** com temática "Copa do Mundo Tech", celebrando pioneiros da tecnologia e IA (Alan Turing, John McCarthy, Guido van Rossum, Linus Torvalds, Steve Jobs, entre outros).

A arquitetura é **fullstack** com separação clara entre frontend e backend:

```
Imersao-072026/
├── FrontEnd/              → Álbum visual interativo (HTML/CSS/JS)
│   ├── index.html         → Estrutura e layout do álbum
│   ├── style.css          → Estilização futurista/espacial
│   ├── app.js             → Lógica de integração com a API
│   └── img/               → Imagens auxiliares do frontend
├── BackEnd/               → API REST em Python (FastAPI + Uvicorn)
│   ├── main.py            → Servidor (endpoints + CORS + estáticos)
│   ├── figurinhas.json    → Dados externalizados (30 figurinhas)
│   ├── figurinhas/        → 30 imagens servidas como estáticos
│   └── .venv/             → Ambiente virtual Python (não versionado)
├── Docs/                  → Documentação do projeto
│   ├── ANALISE_PROJETO.md → Este arquivo
│   └── Prompts            → Histórico de prompts usados nas aulas
├── .gitignore             → Exclusões do versionamento
└── README.md              → Documentação principal do projeto
```

---

## Backend (FastAPI)

### Arquivo: `BackEnd/main.py` (~40 linhas)

| Item | Detalhe |
|------|---------|
| Framework | FastAPI 0.139.0 |
| Servidor | Uvicorn 0.51.0 (ASGI) |
| Python | 3.12.3 |
| Ambiente | `.venv/` (isolado) |
| Porta | 8000 (padrão) |
| CORS | Habilitado (allow_origins=["*"]) |
| Dados | Externalizados em `figurinhas.json` |

### Funcionalidades

- Middleware CORS configurado para permitir acesso cross-origin
- Serve imagens estáticas da pasta `figurinhas/` na rota `/imgs`
- Carrega dados de `figurinhas.json` (30 figurinhas completas)
- Endpoint: `GET /figurinhas` → retorna JSON com lista completa
- Documentação automática em `/docs` (Swagger) e `/redoc`

### Como executar

```bash
cd BackEnd
source .venv/bin/activate
uvicorn main:app --reload
```

Acesse: http://localhost:8000/figurinhas

---

## Frontend (HTML/CSS/JS)

### Arquivos principais

| Arquivo | Função |
|---------|--------|
| `index.html` | Estrutura do álbum com 30 slots, capa com efeito glitch, controles de som e navegação |
| `style.css` | Design "espacial/futurista" com gradientes, sombras 3D, efeito de virar páginas, tema magenta |
| `app.js` | Busca figurinhas via `fetch` na API (`localhost:8000`), preenche slots dinamicamente, controla paginação 3D e sons |

### Fluxo de funcionamento

1. O `app.js` faz um `fetch` para `http://localhost:8000/figurinhas`
2. Recebe a lista de 30 figurinhas em JSON
3. Percorre os slots do HTML e "cola" as imagens correspondentes pelo `id`
4. Aplica classe CSS `slot-preenchido` quando a imagem carrega com sucesso

---

## Repositório

| Item | Detalhe |
|------|---------|
| URL | https://github.com/crfjunior65/Imersao-072026 |
| Visibilidade | Público |
| Branch principal | `main` |
| Hospedagem | GitHub |

---

## Pontos de Atenção — Status

| # | Problema | Status | Resolução |
|---|----------|--------|-----------|
| 1 | Figurinhas incompletas (só 2 de 30) | ✅ Resolvido | Todas as 30 cadastradas no JSON |
| 2 | Imagens duplicadas (`figurinhas-main/`) | ✅ Resolvido | Pasta adicionada ao `.gitignore` |
| 3 | Sem remote Git | ✅ Resolvido | Repo público no GitHub configurado |
| 4 | Arquivos .zip no repositório | ✅ Resolvido | `*.zip` adicionado ao `.gitignore` |
| 5 | Sem CORS configurado | ✅ Resolvido | Middleware CORSMiddleware adicionado |
| 6 | Typo no mount (`name="imga"`) | ✅ Resolvido | Corrigido para `name="imgs"` |
| 7 | Dados hardcoded no código | ✅ Resolvido | Externalizados para `figurinhas.json` |

---

## Evoluções Futuras

| # | Melhoria | Descrição |
|---|----------|-----------|
| 1 | Banco de dados | Migrar `figurinhas.json` para SQLite ou PostgreSQL |
| 2 | Endpoint de busca | `GET /figurinhas?categoria=IA` — filtrar por categoria |
| 3 | Endpoint individual | `GET /figurinhas/{id}` — retornar figurinha específica |
| 4 | Deploy em nuvem | Hospedar backend no Railway/Render e frontend no GitHub Pages |
| 5 | Autenticação | Sistema de login para cada usuário ter seu próprio álbum |
| 6 | Figurinhas repetidas | Lógica de troca de figurinhas entre usuários |
| 7 | Responsividade mobile | Otimizar layout para telas menores |
| 8 | PWA | Transformar em Progressive Web App para instalar no celular |

---

## Stack Tecnológica Completa

| Camada | Tecnologia |
|--------|-----------|
| Frontend | HTML5 + CSS3 + JavaScript (Vanilla) |
| Backend | Python 3.12 + FastAPI + Uvicorn |
| Dados | JSON (arquivo estático) |
| Versionamento | Git + GitHub |
| Gerenciamento de pacotes | pip + venv |
| Documentação | Markdown |

---

## Comandos de Referência

| Ação | Comando |
|------|---------|
| Ativar venv | `cd BackEnd && source .venv/bin/activate` |
| Rodar backend | `uvicorn main:app --reload` |
| Ver docs da API | http://localhost:8000/docs |
| Ver figurinhas | http://localhost:8000/figurinhas |
| Ver imagem | http://localhost:8000/imgs/01-alan-turing.jpg |
| Desativar venv | `deactivate` |
| Git status | `git status` |
| Git push | `git add . && git commit -m "msg" && git push` |
