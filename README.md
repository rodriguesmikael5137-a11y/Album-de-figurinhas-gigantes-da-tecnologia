# Seleção Tech 🚀

Este é o repositório do **Alura Album - Seleção Tech**, uma aplicação web interativa que funciona como um álbum de figurinhas virtual voltado para a história do desenvolvimento de software, reunindo grandes personalidades da tecnologia nacionais e internacionais.

O projeto conta com animação realista em 3D para simular o ato de folhear as páginas do álbum, além de geração dinâmica de áudio sintético para simular o som do papel virando.

---

## 🎯 Objetivo

O principal objetivo deste projeto é proporcionar uma experiência gamificada e nostálgica para os usuários colecionarem figurinhas digitais de grandes ícones da tecnologia (como Alan Turing, Guido van Rossum, Linus Torvalds e educadores brasileiros). 

As figurinhas são carregadas de forma assíncrona a partir de uma API de backend, preenchendo automaticamente os slots numerados do álbum.

---

## 📂 Principais Arquivos e Funcionalidades

### 1. 📄 [index.html](file:///c:/Users/rosil/OneDrive/Área de Trabalho/frontend/index.html)
* **Estrutura do Álbum:** Define a estrutura semântica em HTML5 das páginas do livro virtual (Capa, Páginas do Álbum com grids de figurinhas, Contracapa).
* **Slots de Figurinhas:** Contém elementos com a classe `.sticker-slot` identificados com IDs de `#01` a `#30` que descrevem as posições das figurinhas, nomes dos homenageados e seus papéis históricos.
* **Dependências Externas:** Faz a integração com a biblioteca `page-flip` via CDN para habilitar a física de virada de página, e importa os scripts e folhas de estilo locais.

### 2. 🎨 [style.css](file:///c:/Users/rosil/OneDrive/Área de Trabalho/frontend/style.css)
* **Tema Espacial/Tech:** Usa um esquema de cores moderno em tons de azul escuro, preto e elementos em neon azul/ciano.
* **Efeitos e Animações Premium:**
  * Efeito de texto *glitch* nos títulos principais da capa.
  * Esfera tecnológica 3D pulsante e anéis giratórios construídos com CSS puro.
  * Efeito de dobra e sombras na lombada central do livro para gerar sensação de profundidade tridimensional.
  * Efeito de transição suave (`@keyframes sticker-aparecer`) no momento em que as figurinhas são carregadas e coladas no álbum.
* **Design Responsivo:** Adaptado com media queries para oferecer uma ótima experiência tanto em telas grandes quanto em tablets e smartphones.

### 3. ⚙️ [app.js](file:///c:/Users/rosil/OneDrive/Área de Trabalho/frontend/app.js)
* **Integração com a API:** Possui a função assíncrona `preencherFigurinhas()` que consome o endpoint `/figurinhas` de um servidor backend FastAPI (rodando por padrão em `http://localhost:8000`) para obter as URLs das fotos e injetá-las dinamicamente nos slots correspondentes.
* **Configuração e Física de Dobra:** Inicializa e customiza a biblioteca `St.PageFlip` (dimensões, velocidade do flip, sombras) e estende o suporte nativo a toque e arrasto de páginas com cálculos de arraste customizados.
* **Som de Virada de Página:** Utiliza a *Web Audio API* do navegador para gerar e modular de forma sintética (com ruído branco e filtros de banda) o som dinâmico do papel se movendo, contendo controle de mudo e integração com cliques e teclas direcionais do teclado.

---

## 🛠️ Como Executar o Frontend

1. **Pré-requisito:** Certifique-se de que o backend da aplicação esteja rodando na porta `8000` (ex: `http://localhost:8000/figurinhas`) para carregar as fotos das figurinhas.
2. **Servidor Local:** Para evitar problemas de CORS e garantir que a reprodução de áudio e os scripts rodem perfeitamente, sirva a pasta do frontend usando um servidor local simples, como:
   * A extensão **Live Server** do VS Code.
   * Ou executando o comando Python no terminal dentro da pasta `frontend`:
     ```bash
     python -m http.server 3000
     ```
3. Abra `http://localhost:3000` (ou a porta correspondente) no seu navegador.
