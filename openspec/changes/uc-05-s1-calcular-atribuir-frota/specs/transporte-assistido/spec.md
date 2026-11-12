# Spec Delta

## Purpose

Gerir o motor de cálculo e matching inteligente para atribuição automática de condutores voluntários ou viaturas adaptadas de parceiros com base nas necessidades de mobilidade do utente (UC-05).

## ADDED Requirements

### Requirement: UC-05 Matching inteligente e atribuição automática de recursos de transporte
O sistema SHALL executar o motor de triagem e matching automático para pedidos pendentes, cruzando o perfil e as necessidades de mobilidade do utente com a disponibilidade, localização e características dos condutores voluntários e viaturas adaptadas de parceiros, selecionando o recurso ideal em menos de 5 segundos (UC-05, BR-02, RNF-021).

#### Scenario: CT-05.1 Matching com voluntário de viatura ligeira
- **GIVEN** um pedido "Pendente de Triagem" de um utente com mobilidade ligeira ou deficiência visual
- **WHEN** o algoritmo de matching é executado pelo sistema
- **THEN** o sistema seleciona um condutor voluntário disponível com viatura ligeira, reserva o recurso, notifica o condutor e atualiza o estado do pedido para "Atribuído"

#### Scenario: CT-05.2 Matching com viatura adaptada de parceiro
- **GIVEN** um pedido de um utente dependente de cadeira de rodas pesada ou mobilidade reduzida severa
- **WHEN** o algoritmo de matching é executado pelo sistema
- **THEN** o sistema filtra voluntários comuns e aloca uma viatura adaptada de parceiros disponível (Câmara Municipal / Bombeiros), reservando o recurso e atualizando o estado do pedido para "Atribuído"
