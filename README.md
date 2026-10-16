# Alan Fabrício de Morais Filho

Desenvolvedor de software com foco em Back-end e Full Stack, trabalhando principalmente com JavaScript/TypeScript, Node.js, PostgreSQL e SQL. Também atuo com dados, inteligência artificial e infraestrutura, levando projetos da ideia à produção. Em paralelo, curso duas pós-graduações — em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital — e levo cada uma até projeto publicado, não só até o certificado.

| Projeto | O que é | Stack | Ver |
|---|---|---|---|
| **[Saldo](https://github.com/AlanFMF/Financeiro)** | Controle financeiro web e Android com assistente de IA e sincronização bancária | TypeScript · Fastify · PostgreSQL · React · Capacitor | [App](https://alanfmf.github.io/Financeiro/app/) · [APK](https://alanfmf.github.io/Financeiro/) |
| **[DBO IDLE](https://github.com/AlanFMF/dbo-idle-showcase)** | RPG idle multiplayer que escrevi, publiquei e operei em VPS | Node.js · PostgreSQL · WebSocket · Nginx | [Jogar](https://alanfmf.github.io/dbo-idle-play/play/) |
| **[DBO IDLE — dados](https://github.com/AlanFMF/dbo-idle-data)** | Consultas SQL sobre o banco de produção do jogo | PostgreSQL · SQL · Python · Docker | [Repositório](https://github.com/AlanFMF/dbo-idle-data) |
| **[ElmanGuard](https://github.com/AlanFMF/elman-guard)** | Detecção de intrusões com rede recorrente de Elman, avaliada sem vazamento | Python · TensorFlow/Keras · Streamlit | [App](https://elman-guard-apps4fvjn5n5fsk4kb9v2wv.streamlit.app/) |
| **[Gestão de Tarefas](https://github.com/AlanFMF/app-gestao-tarefas-flutter)** | App de tarefas com autenticação e dados por usuário | Flutter · Dart · Firebase | [Repositório](https://github.com/AlanFMF/app-gestao-tarefas-flutter) |

## Full stack — Saldo

[![CI](https://github.com/AlanFMF/Financeiro/actions/workflows/ci.yml/badge.svg)](https://github.com/AlanFMF/Financeiro/actions/workflows/ci.yml)
[![Android e Pages](https://github.com/AlanFMF/Financeiro/actions/workflows/android.yml/badge.svg)](https://github.com/AlanFMF/Financeiro/actions/workflows/android.yml)

[Financeiro](https://github.com/AlanFMF/Financeiro) — controle de receitas e gastos que nasceu da minha planilha e virou um app que uso no dia a dia: no navegador, instalado como PWA ou como APK no Android. **[Abrir o app](https://alanfmf.github.io/Financeiro/app/)** (tem modo demonstração) · **[Baixar o APK](https://alanfmf.github.io/Financeiro/)**

- **API em Node.js + TypeScript** com Fastify, validação com Zod, JWT, rate limit e PostgreSQL com migrações versionadas. Valores guardados em centavos inteiros, nunca em ponto flutuante.
- **Assistente por chat e voz**: a pessoa escreve ou fala "gastei 45 no mercado e 12 de uber ontem" e os lançamentos entram categorizados. Cada usuário conecta a própria IA — Claude, ChatGPT ou Gemini — por *tool calling*, com a chave cifrada em AES-256-GCM; sem chave, um interpretador por regras resolve valores por extenso, datas relativas e parcelas.
- **Sincronização com o banco via Open Finance**: uma tarefa agendada envia as transações com uma chave de escopo mínimo, e a API concilia com o que já foi lançado à mão, evitando duplicatas.
- **Um código, três entregas**: React + Vite como PWA no GitHub Pages, o mesmo front empacotado com Capacitor em APK, e a API no Render com banco no Neon.
- **109 testes** com Vitest sobre um Postgres em WebAssembly (PGlite), rodando no CI a cada push; o GitHub Actions também gera o APK e publica o site.

## Desenvolvimento e infraestrutura — DBO IDLE

Um RPG idle multiplayer de navegador que escrevi, publiquei e operei sozinho: frontend em ES Modules, backend Node.js com autoridade de servidor, PostgreSQL, WebSocket, pagamentos com Mercado Pago e uma VPS Ubuntu com Nginx, PM2, HTTPS e backup automatizado.

Rodou como piloto fechado por 15 dias em produção, e os números são medidos, não estimados:

| | |
|---|---:|
| Requisições HTTP atendidas | 64.417 |
| Tempo de resposta (mediana) | 58 ms |
| Tabelas em produção | 20 |
| Eventos de segurança registrados | 576 |

- **[dbo-idle-showcase](https://github.com/AlanFMF/dbo-idle-showcase)** — estudo de caso: arquitetura, decisões técnicas, infraestrutura, métricas reais e trechos do código de produção.
- **[dbo-idle-play](https://github.com/AlanFMF/dbo-idle-play)** — a versão jogável, convertida para rodar inteira no navegador depois que o servidor foi desligado. **[Jogar](https://alanfmf.github.io/dbo-idle-play/play/)**
- **[dbo-idle-data](https://github.com/AlanFMF/dbo-idle-data)** — consultas SQL sobre o banco do jogo: economia, retenção, drops, pagamentos e integridade, sobre o schema real e dados sintéticos.

## Inteligência artificial e segurança — ElmanGuard

[![Abrir o app](https://img.shields.io/badge/Streamlit-abrir_o_app-ff4b4b?logo=streamlit&logoColor=white)](https://elman-guard-apps4fvjn5n5fsk4kb9v2wv.streamlit.app/)
[![Testes](https://github.com/AlanFMF/elman-guard/actions/workflows/tests.yml/badge.svg)](https://github.com/AlanFMF/elman-guard/actions/workflows/tests.yml)

[elman-guard](https://github.com/AlanFMF/elman-guard) — detecção de intrusões em tráfego de rede com uma rede recorrente de Elman, sobre o CICIDS2017. [Teste o app online](https://elman-guard-apps4fvjn5n5fsk4kb9v2wv.streamlit.app/), sem instalar nada.

O modelo é a parte fácil. O projeto é sobre saber se ele detecta alguma coisa de verdade:

- **O protocolo de avaliação decide o número.** O mesmo modelo marca PR-AUC de 0,74 com split aleatório, 0,67 com split temporal sem vazamento e 0,34 quando os tipos de ataque são inéditos. No split aleatório, 66% das janelas de teste compartilham algum fluxo com o treino.
- Medido **dentro de cada servidor**, o desempenho diante de ataques inéditos some: quase todo o PR-AUC agregado era reconhecer *qual máquina* enviou a janela.
- Uma **regressão logística vence as redes neurais nos três protocolos**, e com ataques inéditos as quatro redes ficam dentro do próprio ruído entre sementes.
- Antes de concluir que a recorrência não ajuda, o experimento é **aferido numa sonda onde a ordem temporal é o único sinal** — a primeira configuração teria produzido um resultado nulo confiante e falso.

Os detalhes — split cronológico, features que vazam o rótulo, defeitos do dataset corrigidos e cobertos por teste — estão no [README do projeto](https://github.com/AlanFMF/elman-guard).

## Mobile — Gestão de Tarefas

[app-gestao-tarefas-flutter](https://github.com/AlanFMF/app-gestao-tarefas-flutter) — app Flutter com login por e-mail, tarefas salvas por usuário no Cloud Firestore, calendário ligado aos vencimentos e testes de domínio.

## Stack

| Área | Tecnologias |
|---|---|
| **Linguagens** | JavaScript · TypeScript · Python · SQL · PHP · Dart · C |
| **Back-end** | Node.js · Fastify · APIs REST · WebSocket · JWT e sessões · Zod |
| **Banco de Dados** | PostgreSQL · MySQL · modelagem, migrações e consultas SQL · Firebase Firestore |
| **Front-end e mobile** | React · Vite · PWA · Capacitor (Android) · Flutter · HTML · CSS · Canvas 2D · Streamlit |
| **Dados** | Power BI · pandas |
| **IA e Machine Learning** | TensorFlow/Keras · scikit-learn · séries temporais · APIs de LLM com *tool calling* (Claude, OpenAI, Gemini) |
| **Infraestrutura** | Linux · Nginx · PM2 · HTTPS/Certbot · Docker · Render · Neon · GitHub Pages |
| **Qualidade e CI/CD** | Git · GitHub Actions · Vitest · pytest |

## Formação

Bacharel em Sistemas de Informação pela Uniube. Cursando duas pós-graduações, em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital.

## Contato

[LinkedIn](https://www.linkedin.com/in/alanfmf) · alan.fmf@hotmail.com · Uberlândia, MG
