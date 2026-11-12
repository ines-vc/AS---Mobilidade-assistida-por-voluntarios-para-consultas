# Design: UC-05.S1 - Calcular e Atribuir Frota ou Voluntário (Matching Inteligente)

## Context

Ver proposta em `proposal.md`. O motor de matching inteligente (UC-05) constitui o núcleo algorítmico do Pilar 1 da solução, responsável por automatizar a triagem e atribuição de pedidos de transporte "Pendente de Triagem" a voluntários ou viaturas adaptadas de parceiros com base no grau de mobilidade e otimização de rotas.

## Goals / Non-Goals

**Goals:**
- Implementar o algoritmo de matching (peso de pontuação baseado em proximidade geográfica, disponibilidade horária e compatibilidade de grau de mobilidade).
- Suportar o fluxo de priorização de viaturas adaptadas (parceiros como Câmara Municipal / Bombeiros) para utentes com mobilidade severa / cadeira de rodas (Fluxo A1).
- Garantir tempo de execução do algoritmo inferior a 5 segundos (RNF-021).
- Atualizar automaticamente o estado do pedido para "Atribuído" e notificar o recurso alocado.

**Non-Goals:**
- Gestão financeira ou mecânica das viaturas privadas dos voluntários (excluído no SRS).
- Atribuição manual avançada de escala por operadores da IPSS (reservado para faturamentos ou exceções posteriores no UC-07).

## Decisions

- **Decisão 1: Motor de Scoring Ponderado para Matching**
  - *Escolha*: Utilizar um algoritmo de pontuação ponderada que avalia proximidade (via API Google Maps Distance Matrix), compatibilidade de mobilidade (ex: cadeira de rodas exige viatura adaptada) e pontualidade/histórico do voluntário (Banco de Tempo).
  - *Alternativa considerada*: Atribuição estritamente por ordem de chegada (FIFO). Rejeitado por não otimizar a adequação do veículo ao tipo de deficiência e proximidade geográfica.

- **Decisão 2: Execução Assíncrona do Algoritmo**
  - *Escolha*: Executar o matching via job em background ou disparado por webhook imediatamente após a validação do pedido, garantindo resposta rápida ao utilizador e cumprimento do RNF-021 (< 5s).
  - *Alternativa considerada*: Matching síncrono durante o pedido HTTP de submissão. Rejeitado devido ao risco de timeout se as APIs externas de mapas demorarem a responder.

## Risks / Trade-offs

- **[Risco] Indisponibilidade temporária de voluntários ou veículos adaptados na zona** → *Mitigação*: Caso o matching falhe ou não encontre recursos disponíveis no horário, o sistema transita automaticamente para o fluxo de exceção (encaminhamento para operador de recurso / Táxi/TVDE ou acionamento do UC-07).
- **[Risco] Latência na API Google Maps** → *Mitigação*: Implementar caching local de distâncias e coordenadas geográficas das IPSS, unidades de saúde e residências frequentes.
