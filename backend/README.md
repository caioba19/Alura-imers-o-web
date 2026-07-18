# Backend — API Álbum de Figurinhas

API REST que serve os dados e imagens das figurinhas do álbum virtual "Copa do Mundo Tech".

---

## Stack

| Tecnologia | Versão | Papel |
|-----------|--------|-------|
| Python | 3.12 | Linguagem |
| FastAPI | 0.139.0 | Framework web |
| Uvicorn | 0.51.0 | Servidor ASGI |
| Pydantic | 2.13.4 | Validação de dados |
| Starlette | 1.3.1 | Base HTTP do FastAPI |

---

## Estrutura

```
BackEnd/
├── main.py            → Servidor FastAPI (endpoints + CORS + arquivos estáticos)
├── figurinhas.json    → Dados das 30 figurinhas (editável sem alterar código)
├── figurinhas/        → 30 imagens das figurinhas (jpg, jpeg, png, webp, avif)
├── .venv/             → Ambiente virtual Python (não versionado)
└── README.md          → Este arquivo
```

---

## Pré-requisitos

- Python 3.10+ instalado
- Terminal com acesso ao comando `python3` e `pip`

---

## Setup Rápido

```bash
# 1. Entrar na pasta do backend
cd BackEnd

# 2. Criar ambiente virtual (apenas na primeira vez)
python3 -m venv .venv

# 3. Ativar o ambiente virtual
source .venv/bin/activate        # Linux/macOS
# .venv\Scripts\activate.bat     # Windows CMD
# .venv\Scripts\Activate.ps1     # Windows PowerShell

# 4. Instalar dependências
pip install fastapi uvicorn

# 5. Rodar o servidor
uvicorn main:app --reload
```

O servidor inicia em **http://localhost:8000**.

---

## Endpoints

### `GET /figurinhas`

Retorna a lista completa de 30 figurinhas cadastradas em formato JSON.

**Resposta (exemplo):**

```json
[
  {
    "id": 1,
    "nome": "Alan Turing",
    "categoria": "IA",
    "imagem_url": "/imgs/01-alan-turing.jpg"
  },
  {
    "id": 30,
    "nome": "Junior Fernandes",
    "categoria": "SRE/DevOps",
    "imagem_url": "/imgs/30-Junior-Fernandes.png"
  }
]
```

### `GET /imgs/{nome_do_arquivo}`

Serve as imagens estáticas da pasta `figurinhas/`.

**Exemplo:** http://localhost:8000/imgs/01-alan-turing.jpg

---

## Documentação Automática

O FastAPI gera documentação interativa automaticamente:

| Interface | URL |
|-----------|-----|
| Swagger UI | http://localhost:8000/docs |
| ReDoc | http://localhost:8000/redoc |

---

## Configurações do Servidor

### CORS (Cross-Origin Resource Sharing)

O middleware CORS está configurado para permitir acesso de qualquer origem:

```python
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

Isso permite que o frontend (ex: Live Server na porta 5500) acesse a API (porta 8000) sem bloqueio do navegador.

### Dados Externalizados

Os dados das figurinhas ficam no arquivo `figurinhas.json`, separados do código. Para adicionar, remover ou editar figurinhas:

1. Editar `figurinhas.json`
2. Reiniciar o servidor (ou o `--reload` aplica automaticamente)

Não é necessário alterar o `main.py`.

---

## Imagens Disponíveis

A pasta `figurinhas/` contém 30 arquivos de imagem:

| # | Arquivo | Formato |
|---|---------|---------|
| 01 | alan-turing | jpg |
| 02 | john-mccarthy | jpg |
| 03 | sam | jpg |
| 04 | Geoffrey | jpg |
| 05 | Yann | jpeg |
| 06 | Guido | jpg |
| 07 | Tim | jpeg |
| 08 | Ray | jpeg |
| 09 | Travis | jpg |
| 10 | Wes | jpg |
| 11 | Edgar | jpeg |
| 12 | Larry | jpg |
| 13 | Michael | webp |
| 14 | Salvatore | png |
| 15 | Eliot | png |
| 16 | Linus | jpg |
| 17 | Dennis | png |
| 18 | Richard | jpg |
| 19 | bill | jpg |
| 20 | Steve | webp |
| 21 | Paulo | avif |
| 22 | Guilherme | jpeg |
| 23 | Gus | png |
| 24 | Mauricio | jpeg |
| 25 | Andre | jpeg |
| 26 | Guilherme | jpeg |
| 27 | Gi | jpeg |
| 28 | Vinicius | jpeg |
| 29 | Rafa | jpeg |
| 30 | Caio Vinicius | png |

---

## Como funciona

```
┌─────────────┐       GET /figurinhas       ┌──────────────────┐
│  Frontend   │ ──────────────────────────►  │     FastAPI      │
│  (app.js)   │ ◄──────────────────────────  │     main.py      │
└─────────────┘       JSON response          └──────────────────┘
       │                                            │
       │         GET /imgs/01-alan-turing.jpg       │  figurinhas.json
       │ ──────────────────────────────────────────►│  (dados)
       │ ◄──────────────────────────────────────────│
       │              imagem binária                 │
       │                                     ┌──────┴──────┐
       │                                     │ figurinhas/  │
       │                                     │ (30 imgs)    │
       └─────────────────────────────────────┘             │
                                             └─────────────┘
```

1. O `main.py` carrega os dados de `figurinhas.json` na inicialização
2. O frontend faz `fetch` para `/figurinhas` e recebe a lista JSON
3. Para cada figurinha, usa o campo `imagem_url` para carregar a imagem
4. As imagens são servidas pelo FastAPI via `StaticFiles`

---

## Referência

- [FastAPI Docs](https://fastapi.tiangolo.com/)
- [Uvicorn Docs](https://www.uvicorn.org/)
