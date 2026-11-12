# Design: UC-11.S1 - Receber Alerta B2B de Fim de Consulta

## Context
Conforme definido na arquitetura do sistema, a comunicação com os hospitais e centros de saúde é realizada através de uma integração B2B direta com o sistema administrativo da unidade de saúde, evitando a necessidade de hardware proprietário adicional (kiosks) e notificando a plataforma assim que o utente dá entrada ou alta da consulta[cite: 6, 9].

## Goals / Non-Goals
- **Goals:**
  - Processar eventos hospitalares B2B com baixa latência para notificar imediatamente o voluntário[cite: 8, 9].
  - Garantir autenticação e integridade das mensagens enviadas pelas entidades hospitalares.
- **Non-Goals:**
  - Aceder a dados clínicos confidenciais do utente (apenas identificadores anonimizados/referência do agendamento e estado administrativo de entrada/saída).
  - Cálculo de KPIs históricos de tempos de espera (pertence ao UC de Dashboard de Métricas B2B)[cite: 9, 11].

## Decisions
- **Webhook REST Assíncrono com API Key / HMAC:** Expor um endpoint REST JSON dedicado (`/api/b2b/hospital/eventos`) autenticado por credenciais institucionais por unidade de saúde.
- **Correlação por Referência de Agendamento:** O payload B2B identifica a missão através do código de referência de transporte gerado no agendamento, evitando a exposição de dados sensíveis do utente na integração.

## Trade-offs / Risks
- **Trade-off:** Optou-se por integração via webhook HTTP/JSON standard em vez de protocolos hospitalares legados complexos (ex.: HL7v2), facilitando a adoção rápida pelos sistemas administrativos das unidades de saúde.
- **Risk:** Falha temporária na entrega da notificação push ao telemóvel do voluntário. Mitigação: persistir o estado `"Pronto para Recolha"` na base de dados para que a App Móvel reflita a atualização no próximo polling/refresh caso a push falhe.
