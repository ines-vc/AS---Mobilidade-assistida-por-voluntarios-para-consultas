# Proposal: UC-08.S1 - Realizar Missão de Transporte (Fluxo Básico)

## Why
Após a atribuição de uma missão de transporte a um condutor voluntário (UC-05), é necessário permitir o registo operacional das etapas da viagem (recolha do utente, acompanhamento porta-a-porta até à unidade de saúde e conclusão do regresso)[cite: 6, 7, 11]. Além de garantir a rastreabilidade de segurança do utente durante o serviço, a conclusão da missão deve creditar automaticamente as horas dedicadas no Banco de Tempo para valorização e reconhecimento do voluntário[cite: 5, 8, 11].

## What Changes
- Criação da capacidade de **Execução de Missão de Transporte e Crédito no Banco de Tempo** (`execucao-missao`)[cite: 5, 8].
- Implementação da máquina de estados da viagem na App Móvel do Voluntário (`Aceite` -> `Em Recolha` -> `Em Consulta` -> `Em Regresso` -> `Concluído`).
- Cálculo e crédito automático das horas de voluntariado no saldo do Banco de Tempo após a conclusão do transporte de regresso[cite: 5, 8].

## Capabilities
### New Capabilities
- `execucao-missao`: Registo sequencial das etapas da missão de transporte porta-a-porta pelo condutor voluntário e atribuição automática de créditos de horas no Banco de Tempo[cite: 5, 6, 8, 11].

### Modified Capabilities
<!-- Nenhuma capacidade existente modificada -->

## Impact
- **App Móvel (Voluntário):** Novo ecrã de acompanhamento ativo da missão com ações de check-in de recolha, chegada ao hospital e fim de missão[cite: 6, 8].
- **Backend / Domínio:** Novo serviço de gestão de estados de execução de viagem e integração interna com o módulo de Banco de Tempo[cite: 5, 8].
- **Base de Dados:** Registo de timestamps operacionais (`hora_recolha`, `hora_chegada_hospital`, `hora_conclusao`) e lançamentos de crédito no extrato do voluntário.
