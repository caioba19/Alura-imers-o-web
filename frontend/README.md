# Frontend — Álbum de Figurinhas Virtual

Interface interativa do álbum de figurinhas "Copa do Mundo Tech", com efeito de folhear páginas em 3D.

---

## Stack

<p align="left">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white" alt="CSS3">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Google%20Fonts-4285F4?style=flat-square&logo=googlefonts&logoColor=white" alt="Google Fonts">
</p>

---

## Estrutura

```
FrontEnd/
├── index.html     → Estrutura do álbum (capa, páginas, slots, controles)
├── style.css      → Estilização futurista com tema magenta/espacial
├── app.js         → Lógica de integração com a API e controle de páginas
├── img/           → Imagens auxiliares do frontend
└── README.md      → Este arquivo
```

---

## Como Executar

1. Certifique-se de que o **backend está rodando** em `http://localhost:8000`
2. Abra `index.html` no navegador diretamente, ou use a extensão **Live Server** do VS Code
3. O álbum carrega as 30 figurinhas automaticamente

---

## Funcionalidades

| Funcionalidade | Descrição |
|---------------|-----------|
| Paginação 3D | Efeito realista de virar páginas com sombras e transições |
| Carregamento dinâmico | Busca figurinhas da API via `fetch` e preenche os slots |
| Efeitos sonoros | Som de folheamento de páginas (botão para ativar/desativar) |
| Navegação por botões | Setas para avançar e voltar páginas |
| Design responsivo | Adaptável a diferentes tamanhos de tela |
| Efeito glitch | Animação no título da capa |

---

## Entendendo o Papel de Cada Arquivo

Para compreender a divisão de responsabilidades, imagine que estamos construindo um **álbum físico de papel**:

### 📄 `index.html` — A Estrutura

É a folha de papel física. Define **o que** existe na página:
- A capa com o título "ALURA"
- Os quadradinhos vazios (slots) onde cada figurinha será colada
- Os botões de navegação e controle de som
- 30 slots numerados (#01 a #30) distribuídos em 6 páginas

### 🎨 `style.css` — A Estética

É a decoração e personalização do álbum. Define **como** o conteúdo deve parecer:
- Tema espacial com cores escuras e magenta
- Fontes personalizadas (Inter e Outfit via Google Fonts)
- Efeito 3D nas páginas com sombras realistas
- Animações de transição ao virar páginas
- Efeito glitch luminoso no título

### ⚡ `app.js` — A Lógica

É o que faz o álbum ganhar vida. Define **o que a página faz**:
- Conecta com a API (`http://localhost:8000/figurinhas`) via `fetch`
- Percorre os slots do HTML e "cola" as imagens correspondentes pelo `id`
- Controla a navegação (virar páginas com animação)
- Gerencia o som de folheamento
- Trata erros de conexão com a API

---

## Fluxo de Carregamento

```
1. Página carrega (DOMContentLoaded)
       │
2. app.js faz fetch → GET http://localhost:8000/figurinhas
       │
3. Recebe JSON com 30 figurinhas
       │
4. Percorre os slots do HTML (#01 a #30)
       │
5. Para cada slot com figurinha correspondente:
       │   → Cria elemento <img>
       │   → Define src = API_BASE_URL + imagem_url
       │   → Insere no slot
       │
6. Ao carregar a imagem → adiciona classe "slot-preenchido"
```

---

## Slots e Figurinhas

O álbum possui 30 slots distribuídos em 6 páginas internas:

| Página | Slots |
|--------|-------|
| 1-2 | #01 a #10 |
| 3-4 | #11 a #20 |
| 5-6 | #21 a #30 |

Cada slot exibe:
- Número da figurinha (`#01`, `#02`, etc.)
- Nome da personalidade
- Área/cargo

A figurinha #30 é **Junior Fernandes** (SRE/DevOps).

---

## Configuração da API

A URL base da API está definida no `app.js`:

```javascript
const API_BASE_URL = "http://localhost:8000";
```

Se o backend estiver rodando em outra porta, altere essa constante.

---

## Referência

- [Google Fonts — Inter](https://fonts.google.com/specimen/Inter)
- [Google Fonts — Outfit](https://fonts.google.com/specimen/Outfit)
