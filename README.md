# Alan Fabrício de Morais Filho

Desenvolvedor full stack e de IA. Construo aplicações de ponta a ponta — banco de dados, API, interface, testes e deploy — e coloco em produção. Trabalho principalmente com **TypeScript, Node.js, React, Python e PostgreSQL**, integrando LLMs (Claude, ChatGPT e Gemini), RAG e agentes.

Bacharel em Sistemas de Informação pela Uniube, cursando pós-graduação em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital. Antes da tecnologia, atuei com atendimento, treinamento e vendas na Algar — por isso começo pelo problema de quem vai usar.

[LinkedIn](https://www.linkedin.com/in/alanfmf) · alan.fmf@hotmail.com · Uberlândia, MG

## Projetos

| Projeto | O que é | Stack | Ver |
|---|---|---|---|
| **[Saldo](https://github.com/AlanFMF/Financeiro)** | Finanças pessoais web e Android com assistente de IA, conector MCP e sincronização bancária | TypeScript · Fastify · React · PostgreSQL · MCP | [App](https://alanfmf.github.io/Financeiro/app/) · [APK](https://alanfmf.github.io/Financeiro/) |
| **[RAG + agentes](https://github.com/AlanFMF/rag-langgraph-supervisor)** | Responde sobre documentos citando a fonte, com um time de agentes coordenado por supervisor | Python · LangChain · Chroma · LangGraph · LangSmith | [Repositório](https://github.com/AlanFMF/rag-langgraph-supervisor) |
| **[ElmanGuard](https://github.com/AlanFMF/elman-guard)** | Detecção de intrusões com rede recorrente, avaliada sem vazamento | Python · TensorFlow/Keras · Streamlit | [App](https://elman-guard-apps4fvjn5n5fsk4kb9v2wv.streamlit.app/) |
| **[DBO IDLE](https://github.com/AlanFMF/dbo-idle-showcase)** | RPG multiplayer que escrevi, publiquei e operei em VPS | Node.js · PostgreSQL · WebSocket · Nginx | [Jogar](https://alanfmf.github.io/dbo-idle-play/play/) |
| **[DBO IDLE — dados](https://github.com/AlanFMF/dbo-idle-data)** | Análises em SQL sobre o banco do jogo | PostgreSQL · SQL · Python | [Repositório](https://github.com/AlanFMF/dbo-idle-data) |
| **[Gestão de Tarefas](https://github.com/AlanFMF/app-gestao-tarefas-flutter)** | App de tarefas com login e dados por usuário | Flutter · Firebase | [Repositório](https://github.com/AlanFMF/app-gestao-tarefas-flutter) |

## Saldo — finanças pessoais com assistente de IA

[![CI](https://github.com/AlanFMF/Financeiro/actions/workflows/ci.yml/badge.svg)](https://github.com/AlanFMF/Financeiro/actions/workflows/ci.yml)
[![Android e Pages](https://github.com/AlanFMF/Financeiro/actions/workflows/android.yml/badge.svg)](https://github.com/AlanFMF/Financeiro/actions/workflows/android.yml)

Nasceu da minha planilha e virou o app que uso todo dia. **[Abrir o app](https://alanfmf.github.io/Financeiro/app/)** (tem modo demonstração) · **[Baixar o APK](https://alanfmf.github.io/Financeiro/)**

- **Assistente por chat e voz:** "gastei 45 no mercado e 12 de uber ontem" vira lançamentos categorizados. Cada usuário conecta a própria IA (Claude, ChatGPT ou Gemini) por *tool calling*, e a IA só age por ferramentas validadas pela API.
- **Em qualquer lugar:** as mesmas ferramentas servidas por **MCP** como conector do Claude, e bots no **Telegram** e no **WhatsApp**, com áudio transcrito.
- **Open Finance sem duplicatas:** uma tarefa agendada envia as transações do banco e a API concilia com o que já foi lançado à mão.
- **Segurança:** chaves de IA cifradas em AES-256-GCM, tokens de menor privilégio guardados como hash, isolamento por usuário testado e webhooks validados por HMAC.
- **Um código, três entregas:** PWA no GitHub Pages, APK Android com Capacitor e API no Render com banco no Neon.
- **Qualidade:** 218 testes (Vitest sobre PGlite), Playwright num celular emulado, fumaça num PostgreSQL 16 real e APK gerado no CI a cada push.

## IA generativa — RAG e agentes

[![CI](https://github.com/AlanFMF/rag-langgraph-supervisor/actions/workflows/ci.yml/badge.svg)](https://github.com/AlanFMF/rag-langgraph-supervisor/actions/workflows/ci.yml)

Assistente que responde perguntas sobre documentos e cita arquivo e página. Dois modos: RAG simples em LangChain e um time no LangGraph em que um supervisor decide a cada passo entre o agente pesquisador e o redator.

- **RAG com Chroma e ingestão incremental:** IDs determinísticos, então reindexar só processa o que mudou.
- **Supervisor previsível:** saída estruturada, decisões sem LLM quando possível e teto de passos.
- **Avaliado no LangSmith** com LLM-juiz: os dois modos acertaram 9 de 9, e o README explica por que, aqui, o time não compensa o custo extra.
- Provedor trocável (OpenAI, Gemini, Anthropic ou Ollama) e 22 testes no CI sem chave de API.

## IA e segurança — ElmanGuard

[![Abrir o app](https://img.shields.io/badge/Streamlit-abrir_o_app-ff4b4b?logo=streamlit&logoColor=white)](https://elman-guard-apps4fvjn5n5fsk4kb9v2wv.streamlit.app/)
[![Testes](https://github.com/AlanFMF/elman-guard/actions/workflows/tests.yml/badge.svg)](https://github.com/AlanFMF/elman-guard/actions/workflows/tests.yml)

Detecção de intrusões em tráfego de rede (CICIDS2017) com rede recorrente de Elman. O modelo é a parte fácil; o projeto é sobre saber se ele detecta algo de verdade:

- **O protocolo decide o número:** o mesmo modelo marca PR-AUC de 0,74 com split aleatório, 0,67 com split temporal e 0,34 com ataques inéditos.
- **O ganho era reconhecer a máquina, não o ataque**, e uma regressão logística vence as redes neurais nos três protocolos.

## Desenvolvimento e infraestrutura — DBO IDLE

RPG idle multiplayer que escrevi, publiquei e operei sozinho: Node.js com autoridade de servidor, PostgreSQL, WebSocket, pagamentos com Mercado Pago e VPS Ubuntu com Nginx, PM2, HTTPS e backup automatizado. Em 15 dias de piloto em produção: **64.417 requisições**, **mediana de 58 ms**, 20 tabelas e 576 eventos de segurança registrados.

[Estudo de caso](https://github.com/AlanFMF/dbo-idle-showcase) · [Versão jogável](https://github.com/AlanFMF/dbo-idle-play) · [Análises em SQL](https://github.com/AlanFMF/dbo-idle-data)

## Stack

| Área | Tecnologias |
|---|---|
| **Linguagens** | TypeScript · JavaScript · Python · SQL · Dart · PHP · C |
| **Back-end** | Node.js · Fastify · APIs REST · WebSocket · SSE · JWT · Zod |
| **Front-end e mobile** | React · Vite · PWA · Capacitor (Android) · Flutter · Streamlit |
| **Banco de dados** | PostgreSQL · MySQL · Firestore · modelagem, migrações e SQL |
| **IA** | APIs do Claude, OpenAI e Gemini com *tool calling* · MCP · LangChain · LangGraph · LangSmith · RAG com Chroma · TensorFlow/Keras · scikit-learn · pandas |
| **Infraestrutura** | Linux · Nginx · PM2 · HTTPS · Docker · Render · Neon · GitHub Pages |
| **Qualidade e CI/CD** | Git · GitHub Actions · Vitest · Playwright · pytest |
