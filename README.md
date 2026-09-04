# Alan Fabrício de Morais Filho

Desenvolvo aplicações web full stack em JavaScript e Node.js, com PostgreSQL, e cuido também da parte que costuma ficar de fora do portfólio: colocar no ar e manter funcionando. Em paralelo, curso duas pós-graduações — em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital — e levo cada uma até projeto publicado, não só até o certificado.

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

**[elman-guard](https://github.com/AlanFMF/elman-guard)** — detecção de intrusões em tráfego de rede com uma rede recorrente de Elman, sobre o CICIDS2017.

O modelo é a parte fácil. O projeto é sobre saber se ele detecta alguma coisa de verdade:

- Medido **dentro de cada servidor**, onde a identidade do host não carrega informação, o desempenho aparente some — quase todo o PR-AUC agregado era reconhecer *qual máquina* enviou a janela, não identificar o ataque.
- Uma **regressão logística vence todas as arquiteturas neurais**, e as quatro redes testadas ficam dentro do próprio ruído entre sementes (desvio de 0,117 contra diferenças de 0,04 entre elas).
- Antes de reportar que a recorrência não ajuda, o experimento é **aferido numa sonda onde a ordem temporal é o único sinal**. A primeira configuração da rede ficava no acaso ali — teria produzido um resultado nulo confiante e falso. Com a configuração corrigida, ela chega a 0,985.

Onde cada pós aparece:

| Redes neurais | Segurança da informação |
|---|---|
| Rede de Elman em Keras, comparada com MLP e modelo linear sob orçamento de parâmetros equivalente | Fluxos agrupados por host monitorado, que é a visão real de quem opera um IDS |
| Janelamento temporal, normalização causal e split cronológico sem vazamento | IPs, portas e `Flow ID` excluídos das features: nesta captura o endereço do atacante **é** o rótulo |
| PR-AUC e recall a um orçamento fixo de falsos positivos, em vez de acurácia sob desbalanceamento | Avaliação contra tipos de ataque nunca vistos no treino, que é o caso que importa em produção |
| Variância entre sementes tratada como resultado, não como detalhe | Seis defeitos documentados do dataset corrigidos e cobertos por teste |

## Stack

| | |
|---|---|
| **Linguagens** | JavaScript · SQL · Python · Dart · PHP · C |
| **Back-end** | Node.js · APIs REST · WebSocket · autenticação e sessões |
| **Dados** | PostgreSQL · MySQL · modelagem e consultas · Power BI · pandas |
| **Machine learning** | TensorFlow/Keras · scikit-learn · séries temporais · avaliação e validação de modelos |
| **Infra** | Linux · Nginx · PM2 · HTTPS/Certbot · Git |
| **Front-end** | HTML · CSS · JavaScript (ES Modules) · Canvas 2D · Streamlit |

## Formação

Bacharel em Sistemas de Informação pela Uniube. Cursando duas pós-graduações, em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital, ambas com conclusão prevista para dezembro de 2026.

## Contato

[LinkedIn](https://www.linkedin.com/in/alanfmf) · alan.fmf@hotmail.com · Uberlândia, MG
