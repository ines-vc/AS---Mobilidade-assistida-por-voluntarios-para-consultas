# Proposal: UC-11.S1 - Receber Alerta B2B de Fim de Consulta (Fluxo Básico)

## Why
Um dos maiores pontos de fricção para condutores voluntários e frotas adaptadas é a incerteza sobre a duração das consultas médicas, resultando em longos tempos de espera improdutivos nos hospitais[cite: 7, 8]. A integração B2B direta com os sistemas das Unidades de Saúde (SNS) permite receber notificações automáticas de entrada e saída da consulta, otimizando o momento exato da recolha de regresso[cite: 6, 8, 9, 11].

## What Changes
- Criação da capacidade de **Integração Hospitalar B2B e Notificação de Fim de Consulta** (`integracao-hospitalar-b2b`)[cite: 5, 6, 9, 11].
- Implementação de um endpoint webhook/API B2B autenticado para receção de eventos clínicos operacionais (`ENTRADA_CONSULTA` e `FIM_CONSULTA`) enviados pelo sistema hospitalar[cite: 6, 9, 11].
- Disparo automático de notificação push em tempo real para a App do Voluntário (ou portal do parceiro de frota) quando o utente conclui a consulta[cite: 7, 8].

## Capabilities
### New Capabilities
- `integracao-hospitalar-b2b`: Receção e processamento de eventos B2B provenientes de unidades de saúde (entrada e fim de consulta) com notificação imediata ao recurso de transporte alocado[cite: 6, 9, 11].

### Modified Capabilities
<!-- Nenhuma capacidade existente modificada -->

## Impact
- **API / Integrações Externas:** Novo endpoint B2B seguro (`POST /api/b2b/hospital/eventos`) com validação de chave/token institucional[cite: 9, 11].
- **Backend / Notificações:** Serviço de processamento de eventos hospitalares e integração com serviço de Push Notifications para a App Móvel[cite: 8].
- **Base de Dados:** Registo de eventos B2B recebidos e atualização do estado operacional do utente para `"Pronto para Recolha"`.
