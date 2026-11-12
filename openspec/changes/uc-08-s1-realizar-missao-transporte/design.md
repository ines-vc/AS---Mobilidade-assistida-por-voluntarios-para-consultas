# Design: UC-08.S1 - Realizar Missão de Transporte

## Context
Os condutores voluntários utilizam a aplicação móvel para gerir as missões aceites[cite: 6, 8]. Para garantir segurança ao utente (especialmente idosos ou pessoas com deficiência visual que necessitam de acompanhamento porta-a-porta) e alimentar o sistema de reconhecimento de voluntários, cada etapa da viagem deve ser registada de forma simples e auditável[cite: 5, 6, 8].

## Goals / Non-Goals
- **Goals:**
  - Permitir a transição simples e sequencial dos estados da viagem pelo voluntário.
  - Garantir que o crédito no Banco de Tempo ocorre de forma idempotente apenas quando a missão é efetivamente concluída[cite: 5, 8].
- **Non-Goals:**
  - Rastreamento GPS contínuo em segundo plano (pertence a um slice/UC dedicado de telemetria).
  - Troca ou resgate de saldo do Banco de Tempo por benefícios locais/vouchers (UC distinto no Épico #3)[cite: 8, 11].

## Decisions
- **Máquina de Estados Estrita no Backend:** Validar no servidor que as transições seguem rigorosamente a ordem `Aceite -> Em Recolha -> Em Consulta -> Em Regresso -> Concluído`, impedindo saltos inválidos ou conclusões duplicadas.
- **Cálculo Idempotente de Créditos:** Utilizar o identificador único da missão (`missao_id`) como chave de idempotência na tabela de movimentos do Banco de Tempo para impedir créditos duplicados em caso de reenvio de pedido pela rede móvel.

## Trade-offs / Risks
- **Trade-off:** Optou-se por check-ins explícitos via botão na app em vez de geofencing automático por GPS para reduzir o consumo de bateria e garantir que o acompanhamento porta-a-porta (dentro do edifício/consultório) é confirmado pelo voluntário[cite: 6].
- **Risk:** Perda momentânea de rede móvel no interior do hospital durante o check-in. Mitigação: guardar o timestamp local no dispositivo e sincronizar assim que a ligação restabelecer.
