# Delta Specification: execucao-missao

## Purpose
Definir os requisitos funcionais e cenários de aceitação para o registo da execução porta-a-porta de uma missão de transporte por um condutor voluntário e respetivo crédito no Banco de Tempo no âmbito do Slice UC-08.S1[cite: 5, 6, 8, 11].

## ADDED Requirements

### Requirement: Registo Sequencial das Etapas da Missão
The system SHALL allow an assigned volunteer driver to record the sequential milestones of a transport mission (beneficiary pickup, arrival at the healthcare unit, and completion of the return trip)[cite: 6, 8, 11].

#### Scenario: CT-08.1 - Execução completa com sucesso
- **GIVEN** uma missão no estado `"Atribuído"` e aceite pelo condutor voluntário no horário agendado
- **WHEN** o voluntário regista a recolha do utente no domicílio, a chegada à unidade de saúde (com acompanhamento porta-a-porta) e, após a consulta, a conclusão do transporte de regresso[cite: 6, 7]
- **THEN** o sistema atualiza o estado do pedido de transporte para `"Concluído"`
- **AND** regista os timestamps de cada etapa da missão.

### Requirement: Crédito Automático no Banco de Tempo
The system SHALL automatically calculate the duration of the completed mission and credit the corresponding hours to the volunteer driver's Time Bank balance upon mission completion[cite: 5, 8].

#### Scenario: CT-08.2 - Atribuição de horas no Banco de Tempo após conclusão
- **GIVEN** uma missão de transporte que transitou para o estado `"Concluído"` com timestamps válidos de início e fim
- **WHEN** o evento de conclusão da missão é processado
- **THEN** o sistema calcula o tempo total dedicado pelo voluntário
- **AND** credita automaticamente essas horas no saldo do Banco de Tempo do voluntário[cite: 5, 8].
