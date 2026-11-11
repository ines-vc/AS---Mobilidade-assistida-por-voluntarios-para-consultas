# Spec Delta

## Purpose

Gerir o fluxo de solicitação de transporte assistido "porta-a-porta" para consultas médicas não urgentes, garantindo a validação de elegibilidade social (BR-03), verificação da antecedência mínima de agendamento (BR-01) e tempos de resposta optimizados (< 2s, RNF-02).

## ADDED Requirements

### Requirement: UC-01 Solicitar transporte assistido com antecedência
O sistema SHALL permitir que um utente elegível autenticado ou técnico social submeta um pedido de transporte assistido "porta-a-porta" para uma consulta médica não urgente com pelo menos 24 horas de antecedência, registando o pedido no estado "Pendente de Triagem" com tempo de resposta inferior a 2 segundos (BR-01, BR-03, RNF-02).

#### Scenario: CT-01.1 Agendamento válido com antecedência
- **GIVEN** um utente elegível autenticado na plataforma e uma consulta marcada para daqui a 48 horas
- **WHEN** submete um pedido indicando ponto de recolha, destino e condicionantes de mobilidade
- **THEN** o pedido é registado com o estado "Pendente de Triagem" e é emitida notificação de confirmação

### Requirement: UC-01 Validação de elegibilidade social na submissão
O sistema SHALL recusar a submissão de um pedido de transporte assistido e informar que o perfil não possui elegibilidade social ativa caso o utente não esteja devidamente validado por uma IPSS parceira (BR-03).

#### Scenario: CT-01.3 Submissão por utente sem elegibilidade social
- **GIVEN** um utilizador autenticado cujo perfil não está sinalizado/validado por nenhuma IPSS parceira
- **WHEN** tenta submeter um pedido de transporte assistido
- **THEN** o sistema recusa a submissão e informa que o perfil não possui elegibilidade social ativa
