# Alan Fabrício de Morais Filho

Desenvolvedor de software com foco em Back-end e Full Stack, trabalhando principalmente com JavaScript, Node.js, PostgreSQL e SQL. Também atuo com dados, inteligência artificial e infraestrutura, levando projetos da ideia à produção. Em paralelo, curso duas pós-graduações — em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital — e levo cada uma até projeto publicado, não só até o certificado.

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
- **[dbo-idle-data](https://github.com/AlanFMF/dbo-idle-data)** — consultas SQL sobre o banco do jogo.

## Inteligência artificial e segurança — ElmanGuard

[![Abrir o app](https://img.shields.io/badge/Streamlit-abrir_o_app-ff4b4b?logo=streamlit&logoColor=white)](https://elman-guard-apps4fvjn5n5fsk4kb9v2wv.streamlit.app/)
[![Testes](https://github.com/AlanFMF/elman-guard/actions/workflows/tests.yml/badge.svg)](https://github.com/AlanFMF/elman-guard/actions/workflows/tests.yml)

[elman-guard](https://github.com/AlanFMF/elman-guard) — detecção de intrusões em tráfego de rede com uma rede recorrente de Elman, sobre o CICIDS2017. [Teste o app online](https://elman-guard-apps4fvjn5n5fsk4kb9v2wv.streamlit.app/), sem instalar nada.

O modelo é a parte fácil. O projeto é sobre saber se ele detecta alguma coisa de verdade:

- **O protocolo de avaliação decide o número.** O mesmo modelo marca PR-AUC de 0,74 com split aleatório, 0,67 com split temporal sem vazamento e 0,34 quando os tipos de ataque são inéditos. No split aleatório, 66% das janelas de teste compartilham algum fluxo com o treino.
- Medido **dentro de cada servidor**, onde a identidade do host não carrega informação, o desempenho diante de ataques inéditos some: quase todo o PR-AUC agregado era reconhecer *qual máquina* enviou a janela. Com tipos de ataque já vistos, a detecção dentro do host se sustenta (ROC-AUC de 0,82 a 0,93).
- Uma **regressão logística vence as redes neurais nos três protocolos**. Com ataques inéditos, as quatro redes ficam dentro do próprio ruído entre sementes (desvio de 0,117 contra diferenças de 0,04 entre elas).
- Na **classificação de 12 tipos de tráfego**, a Elman supera um MLP do mesmo tamanho (F1 macro de 0,71 contra 0,63). Mas embaralhar a ordem dos fluxos não a piora: a vantagem vem de compartilhar pesos ao longo da janela, não de memória.
- Antes de reportar que a recorrência não ajuda, o experimento é **aferido numa sonda onde a ordem temporal é o único sinal**. A primeira configuração da rede ficava no acaso ali — teria produzido um resultado nulo confiante e falso. Com a configuração corrigida, ela chega a 0,985.

Onde cada pós aparece:

| Redes neurais | Segurança da informação |
|---|---|
| Rede de Elman em Keras, comparada com MLP e modelo linear sob orçamento de parâmetros equivalente | Fluxos agrupados por host monitorado, que é a visão real de quem opera um IDS |
| Janelamento temporal, normalização causal e split cronológico sem vazamento | IPs, portas e `Flow ID` excluídos das features: nesta captura o endereço do atacante *é* o rótulo |
| PR-AUC e recall a um orçamento fixo de falsos positivos, em vez de acurácia sob desbalanceamento | Avaliação contra tipos de ataque nunca vistos no treino, que é o caso que importa em produção |
| Variância entre sementes tratada como resultado, não como detalhe | Seis defeitos documentados do dataset corrigidos e cobertos por teste |
| Classificação multiclasse com F1 macro e teste de embaralhamento da ordem | Três protocolos de avaliação, com o vazamento entre treino e teste medido fluxo a fluxo |

## Stack

| Área | Tecnologias |
|---|---|
| **Linguagens** | JavaScript · Python · PHP · Dart · C |
| **Back-end** | Node.js · APIs REST · WebSocket · autenticação e sessões |
| **Banco de Dados** | SQL · PostgreSQL · MySQL · modelagem e consultas SQL |
| **Dados** | Power BI · pandas |
| **Machine Learning** | TensorFlow/Keras · scikit-learn · séries temporais · avaliação e validação de modelos |
| **Infraestrutura** | Linux · Nginx · PM2 · HTTPS/Certbot · Git · GitHub Actions · pytest |
| **Front-end** | HTML · CSS · JavaScript (ES Modules) · Canvas 2D · Streamlit |

## Formação

Bacharel em Sistemas de Informação pela Uniube. Cursando duas pós-graduações, em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital.

## Contato

[LinkedIn](https://www.linkedin.com/in/alanfmf) · alan.fmf@hotmail.com · Uberlândia, MG
