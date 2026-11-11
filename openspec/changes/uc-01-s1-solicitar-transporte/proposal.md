# Proposal: UC-01.S1 - Solicitar Transporte Assistido

## Why

Atualmente, utentes seniores ou com mobilidade reduzida enfrentam barreiras significativas para agendar deslocações seguras e humanizadas para consultas médicas não urgentes. O Slice UC-01.S1 implementa o fluxo básico (passos 1 a 6) de submissão de pedidos de transporte assistido "porta-a-porta", garantindo a verificação prévia de elegibilidade social (BR-03), o cumprimento da antecedência mínima de agendamento (BR-01) e uma resposta célere do sistema (< 2s, RNF-02), permitindo canalizar pedidos de forma estruturada para triagem.

## What Changes

- **Nova Capacidade de Solicitação de Transporte**: Introdução do fluxo para utentes elegíveis e técnicos sociais submeterem pedidos de transporte assistido "porta-a-porta".
- **Validação de Elegibilidade Social**: Verificação obrigatória de que o utente está associado a uma IPSS parceira / entidade validada (BR-03).
- **Validação de Antecedência**: Verificação de que o pedido cumpre a antecedência mínima de 24 horas para agendamento normal (BR-01).
- **Registo e Confirmação**: Registo do pedido no estado "Pendente de Triagem" com emissão de notificação de confirmação e tempo de resposta otimizado (< 2s, RNF-02).

## Capabilities

### New Capabilities
- `transporte-assistido`: Gestão da submissão, validação de elegibilidade, verificação de antecedência e registo inicial de pedidos de transporte assistido (UC-01.S1).

### Modified Capabilities
- (Nenhuma)

## Impact

- **Módulos / Componentes**: Portal Web (para técnicos sociais/IPSS) e App Móvel (para utentes).
- **APIs / Base de Dados**: Novas tabelas/entidades para `PedidoTransporte`, validação de vínculos institucionais (`Utente` e `IPSSParceira`), e serviços de validação de regras de negócio (BR-01, BR-03).
- **Dependências**: Nenhuma dependência externa nova além do ecossistema existente.
