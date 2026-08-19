# 🤖 Agente de IA para Carreira Profissional

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Gemini API](https://img.shields.io/badge/Gemini_API-8E75B2?style=for-the-badge&logo=google-gemini&logoColor=white)](https://ai.google.dev/)
[![POO](https://img.shields.io/badge/Paradigma-POO-563D7C?style=for-the-badge)](#)

## 🎯 Sobre o Projeto

Este projeto une **Programação Orientada a Objetos** e um **agente de Inteligência Artificial** para gerar recomendações personalizadas de progressão de carreira profissional.

A proposta nasceu de um problema simples: acompanhar a evolução de carreira de um profissional exige cruzar informações de perfil (formação, experiências, objetivos) com uma análise que normalmente só um mentor humano conseguiria fazer. Aqui, esse papel de análise é feito por um agente conectado à **API do Gemini**, que recebe os dados estruturados do usuário e devolve recomendações práticas e personalizadas.

## 🧠 Como Funciona

O fluxo do sistema é dividido em três camadas:

1. **Camada de Domínio (POO)** — `usuarios.py` define a classe `Usuario`, responsável por representar o perfil de cada pessoa (atributos e métodos relacionados aos seus dados de carreira).
2. **Camada de Persistência** — `repositorio.py` define a classe `Repositorio`, responsável por armazenar, cadastrar e consultar os usuários registrados no sistema.
3. **Camada de Orquestração e IA** — `gs2-alexandre.py` é o ponto de entrada do programa: apresenta o menu, coleta os dados via as classes acima e envia o contexto do usuário para o **agente de IA (Gemini API)**, que retorna as recomendações de carreira.

Essa separação de responsabilidades (dados vs. lógica vs. IA) foi uma escolha proposital para manter o código organizado e fácil de estender — por exemplo, trocar o provedor de IA no futuro exigiria mudanças isoladas na camada de orquestração, sem tocar nas classes de domínio.

## 🛠️ Tecnologias Utilizadas

- **Python** — linguagem principal do projeto
- **Google Gemini API** — modelo de linguagem responsável por gerar as recomendações
- **Programação Orientada a Objetos** — organização do domínio (usuários e repositório)
- **python-dotenv** — gerenciamento de variáveis de ambiente (chave de API)

## 📁 Estrutura do Projeto

```
Agente-para-carreira-profissional/
│
├── gs2-alexandre.py     # Arquivo principal: menu, orquestração e chamada ao agente de IA
├── usuarios.py          # Classe Usuario — representa o perfil do usuário
├── repositorio.py       # Classe Repositorio — cadastro e gerenciamento dos usuários
├── requirements.txt     # Dependências do projeto
├── .env                 # Variáveis de ambiente (chave da API Gemini) — não versionado
└── README.md            # Este documento
```

## 🚀 Como Executar

### 1. Crie e ative o ambiente virtual

```bash
python -m venv .venv
```

Windows:
```bash
.\.venv\Scripts\activate
```

### 2. Instale as dependências

```bash
pip install -r requirements.txt
```

### 3. Configure sua chave de API

Gere uma chave gratuita no [Google IA Studio](https://aistudio.google.com/api-keys) e crie um arquivo `.env` na raiz do projeto:

```
GEMINI_API_KEY = "sua_key_aqui"
```

### 4. Execute o programa

```bash
python gs2-alexandre.py
```

## 🎥 Demonstração

Vídeo com o sistema em funcionamento: [assista aqui](https://www.youtube.com/watch?v=xyBmeDp5Gjo)

## 🔭 Próximos Passos

Algumas melhorias que pretendemos (ou que fariam sentido) implementar:

- **Persistência real de dados**: hoje o cadastro de usuários vive em memória durante a execução — o próximo passo natural é persistir em arquivo (JSON/SQLite) ou banco de dados.
- **Histórico de recomendações**: guardar as sugestões geradas pelo agente ao longo do tempo, permitindo acompanhar a evolução do usuário.
- **Tratamento de erros da API**: adicionar tratativas para falhas de conexão ou limite de requisições ao Gemini.
- **Testes automatizados**: cobrir as classes `Usuario` e `Repositorio` com testes unitários.
- **Interface web ou CLI mais rica**: hoje o fluxo é via terminal; uma interface simples tornaria a demonstração mais acessível.

## 👥 Equipe

Projeto desenvolvido para a disciplina de Compilado de Programação de Algoritmos e Estrutura de Dados (FIAP) — Turma 1CCPH:

- Fernando Caires Silva — RM 563415
- Raphael Mischiatti de Souza — RM 563567
- Guilherme Martins Rezende — RM 563500

---
Desenvolvido para a Faculdade de Informática e Administração Paulista (FIAP).