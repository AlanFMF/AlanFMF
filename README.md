# Alan Fabrício de Morais Filho

Desenvolvo aplicações web full stack em JavaScript e Node.js, com PostgreSQL, e cuido também da parte que costuma ficar de fora do portfólio: colocar no ar e manter funcionando.

## Projeto em destaque — DBO IDLE

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

O que aprendi ali não foi só escrever o jogo: foi descobrir que o servidor precisa desconfiar do cliente, que um WebSocket ocioso morre em 60 segundos se ninguém configurar o proxy, e que um backup sem teste de restauração é só uma esperança.

## Stack

**Linguagens** JavaScript · SQL · Python · Dart · PHP · C
**Back-end** Node.js · APIs REST · WebSocket · autenticação e sessões
**Dados** PostgreSQL · MySQL · modelagem e consultas · Power BI
**Infra** Linux · Nginx · PM2 · HTTPS/Certbot · Git
**Front-end** HTML · CSS · JavaScript (ES Modules) · Canvas 2D

## Formação

Bacharel em Sistemas de Informação pela Uniube. Cursando duas pós-graduações, em Inteligência Artificial e Redes Neurais e em Segurança da Informação e Forense Digital, ambas com conclusão prevista para dezembro de 2026.

## Contato

[LinkedIn](https://www.linkedin.com/in/alanfmf) · Uberlândia, MG
