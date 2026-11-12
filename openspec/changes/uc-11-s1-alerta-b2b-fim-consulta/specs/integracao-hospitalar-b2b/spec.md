# Delta Specification: integracao-hospitalar-b2b

## Purpose
Definir os requisitos funcionais e cenários de aceitação para a receção de eventos B2B de fim de consulta enviados pelo sistema hospitalar e consequente alerta ao condutor voluntário no âmbito do Slice UC-11.S1[cite: 6, 9, 11].

## ADDED Requirements

### Requirement: Receção de Evento B2B de Fim de Consulta
The system SHALL expose an authenticated B2B API endpoint to receive consultation status events ("ENTRADA_CONSULTA" and "FIM_CONSULTA") from integrated Healthcare Units (SNS) and update the beneficiary's transport status accordingly[cite: 6, 9, 11].

#### Scenario: CT-11.1 - Notificação de fim de consulta via API B2B
- **GIVEN** um utente em consulta numa unidade de saúde integrada com uma missão de transporte de regresso ativa
- **WHEN** o sistema hospitalar envia um evento B2B autenticado do tipo `"FIM_CONSULTA"` para a plataforma[cite: 9, 11]
- **THEN** o sistema atualiza o estado do transporte do utente para `"Pronto para Recolha"`
- **AND** envia uma notificação em tempo real para o condutor voluntário ou operador de frota responsável pelo regresso[cite: 7, 8].

### Requirement: Rejeição de Eventos B2B Não Autenticados
The system SHALL reject any incoming B2B hospital event request that lacks valid institutional API credentials.

#### Scenario: CT-11.2 - Tentativa de envio de evento B2B sem credenciais válidas
- **GIVEN** uma requisição enviada ao endpoint B2B hospitalar sem token/API key válida da unidade de saúde
- **WHEN** o endpoint processa o pedido
- **THEN** o sistema rejeita o pedido com código HTTP `401 Unauthorized`
- **AND** não altera o estado de nenhuma missão ativa.
