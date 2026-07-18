# 🏆 Álbum de Figurinhas Virtual 
#    Copa do Mundo Tech(Imersão Alura)

<p align="center">
  <img src="https://img.shields.io/badge/status-em%20desenvolvimento-yellow?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/imersão-Alura%2007%2F2026-blue?style=for-the-badge" alt="Imersão Alura">
  <img src="https://img.shields.io/github/last-commit/crfjunior65/Imersao-072026?style=for-the-badge" alt="Last Commit">
</p>

<p align="center">
  Álbum de figurinhas interativo celebrando os pioneiros e gigantes da tecnologia e Inteligência Artificial.
</p>

---

## 🛠️ Tecnologias Utilizadas

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/Uvicorn-2C2C2C?style=for-the-badge&logo=uvicorn&logoColor=white" alt="Uvicorn">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white" alt="JSON">
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git">
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
</p>

---

## 📖 Sobre o Projeto

Este projeto faz parte da **Imersão Alura 07/2026** e simula a experiência de um álbum de figurinhas físico em formato digital. O álbum contém **30 figurinhas** de personalidades marcantes da história da tecnologia — de Alan Turing e Linus Torvalds até instrutores da Alura.

### ✨ Funcionalidades

- 📖 **Simulação realista** — Efeito 3D de folhear páginas com transições e sombras
- 🔗 **Integração Frontend ↔ Backend** — Dados carregados dinamicamente via API REST
- 🖼️ **Servir imagens estáticas** — Imagens servidas diretamente pelo FastAPI
- 🔊 **Efeitos sonoros** — Som de folheamento de páginas (ativar/desativar)
- 🎨 **Design futurista** — Tema espacial com gradientes, brilho 3D e efeito glitch
- 🌐 **CORS configurado** — Frontend e backend podem rodar em portas diferentes
- 📄 **Dados externalizados** — Figurinhas em arquivo JSON editável sem tocar no código

---

## 🏗️ Arquitetura

```
┌─────────────────────────────────────────────────────────┐
│                      FRONTEND                           │
│  ┌──────────┐  ┌──────────┐  ┌──────────────────────┐  │
│  │index.html│  │style.css │  │       app.js         │  │
│  │Estrutura │  │ Estética │  │ Lógica + fetch API   │  │
│  └──────────┘  └──────────┘  └───────────┬──────────┘  │
└───────────────────────────────────────────┼─────────────┘
                                            │
                              GET /figurinhas│  GET /imgs/*
                                            ▼
┌─────────────────────────────────────────────────────────┐
│                       BACKEND                           │
│  ┌──────────┐  ┌────────────────┐  ┌────────────────┐  │
│  │ main.py  │  │figurinhas.json │  │  figurinhas/   │  │
│  │ FastAPI  │  │   30 itens     │  │  30 imagens    │  │
│  └──────────┘  └────────────────┘  └────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## 📁 Estrutura do Projeto

```
Imersao-072026/
├── BackEnd/
│   ├── main.py              → Servidor FastAPI (endpoints + CORS + estáticos)
│   ├── figurinhas.json      → Dados das 30 figurinhas (editável)
│   ├── figurinhas/          → 30 imagens (jpg, jpeg, png, webp, avif)
│   └── README.md            → Documentação específica do backend
├── FrontEnd/
│   ├── index.html           → Estrutura do álbum com slots numerados
│   ├── style.css            → Estilização futurista com tema magenta
│   ├── app.js               → Lógica de integração com a API
│   ├── img/                 → Imagens auxiliares do frontend
│   └── README.md            → Documentação específica do frontend
├── Docs/
│   ├── ANALISE_PROJETO.md   → Análise técnica completa do projeto
│   └── Prompts              → Histórico de prompts usados nas aulas
├── .gitignore               → Arquivos excluídos do versionamento
└── README.md                → Este arquivo
```

---

## 🚀 Como Executar

### Pré-requisitos

- **Python 3.10+** instalado
- **Git** instalado
- Navegador moderno (Chrome, Firefox, Edge)

### 1. Clonar o repositório

```bash
git clone https://github.com/crfjunior65/Imersao-072026.git
cd Imersao-072026
```

### 2. Configurar e rodar o Backend

```bash
cd BackEnd

# Criar ambiente virtual
python3 -m venv .venv

# Ativar ambiente virtual
source .venv/bin/activate        # Linux/macOS
# .venv\Scripts\activate.bat     # Windows CMD
# .venv\Scripts\Activate.ps1     # Windows PowerShell

# Instalar dependências
pip install fastapi uvicorn

# Rodar o servidor
uvicorn main:app --reload
```

O servidor inicia em **http://localhost:8000**

### 3. Abrir o Frontend

Abra o arquivo `FrontEnd/index.html` no navegador, ou use a extensão **Live Server** do VS Code.

### 4. Pronto! 🎉

O álbum carrega as 30 figurinhas automaticamente da API.

---

## 🔗 Endpoints da API

| Método | Rota | Descrição |
|--------|------|-----------|
| `GET` | `/figurinhas` | Retorna a lista completa de figurinhas em JSON |
| `GET` | `/imgs/{arquivo}` | Serve uma imagem estática da pasta figurinhas |
| `GET` | `/docs` | Documentação interativa Swagger UI |
| `GET` | `/redoc` | Documentação alternativa ReDoc |

---

## 🎴 Figurinhas do Álbum

| # | Nome | Categoria |
|---|------|-----------|
| 01 | Alan Turing | IA |
| 02 | John McCarthy | IA |
| 03 | Sam Altman | IA |
| 04 | Geoffrey Hinton | IA |
| 05 | Yann LeCun | IA |
| 06 | Guido van Rossum | Linguagens |
| 07 | Tim Berners-Lee | Web |
| 08 | Ray Kurzweil | IA |
| 09 | Travis Kalanick | Empresas |
| 10 | Wes McKinney | Dados |
| 11 | Edgar Codd | Dados |
| 12 | Larry Page | Empresas |
| 13 | Michael Stonebraker | Dados |
| 14 | Salvatore Sanfilippo | Dados |
| 15 | Eliot Horowitz | Dados |
| 16 | Linus Torvalds | SO |
| 17 | Dennis Ritchie | Linguagens |
| 18 | Richard Stallman | SO |
| 19 | Bill Gates | Empresas |
| 20 | Steve Jobs | Empresas |
| 21 | Paulo Silveira | Alura |
| 22 | Guilherme Silveira | Alura |
| 23 | Gus Guanabara | Educação |
| 24 | Maurício de Nassau | Alura |
| 25 | André Noel | Alura |
| 26 | Guilherme Lima | Alura |
| 27 | Giovanna Moeller | Alura |
| 28 | Vinícius Neves | Alura |
| 29 | Rafa Ballerini | Alura |
| 30 | Caio Vinicius | SRE/DevOps |

---

## 📚 Documentação

| Documento | Descrição |
|-----------|-----------|
| [backend/README.md](backend/README.md) | Documentação técnica da API |
| [frontend/README.md](frontend/README.md) | Explicação didática do frontend |
| [Docs/ANALISE_PROJETO.md](Docs/ANALISE_PROJETO.md) | Análise técnica e pontos de evolução |
| [Docs/Prompts](Docs/Prompts) | Histórico de prompts usados nas aulas |

---

## 🧑‍💻 Autor

**Caio Vinicius** — SRE/DevOps

[![GitHub](https://img.shields.io/badge/GitHub-caioba19-181717?style=flat-square&logo=github)](https://github.com/caioba19)

---

## 📝 Licença

Este projeto foi desenvolvido para fins educacionais durante a Imersão Alura 07/2026.
