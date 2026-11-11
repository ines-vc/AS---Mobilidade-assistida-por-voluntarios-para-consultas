# Design: UC-01.S1 - Solicitar Transporte Assistido

## Context

Ver a proposta em `proposal.md` para a motivação de negócio e o âmbito do Slice UC-01.S1. O sistema requer a criação do fluxo de submissão de pedidos de transporte assistido com validação de elegibilidade social (BR-03) e de antecedência mínima de 24h (BR-01), com tempo de resposta inferior a 2s (RNF-02).

## Goals / Non-Goals

**Goals:**
- Implementar o endpoint/serviço de submissão de `PedidoTransporte` com validação síncrona de elegibilidade do utente (`Utente` com vínculo a `IPSSParceira`) e cálculo de antecedência da `ConsultaMedica`.
- Registar o pedido com o estado inicial "Pendente de Triagem".
- Garantir validações de acessibilidade e usabilidade (WCAG 2.1 AA) e desempenho de resposta (< 2s, RNF-02).

**Non-Goals:**
- Atribuição automática de voluntário ou frota (tratado no UC-05).
- Gestão de cancelamento de pedidos (tratado no UC-04).
- Integração com operadores de recurso (Táxi/TVDE).

## Decisions

- **Arquitetura e Camadas**: Abordagem em API REST / Backend modular em serviço Node.js / Python com frontend multi-canal (Portal Web para técnicos sociais e App Móvel para utentes).
- **Validação de Elegibilidade (BR-03)**: Verificação relacional na base de dados validando se o ID do utente possui registo ativo associado a uma IPSS parceira.
- **Validação de Antecedência (BR-01)**: Verificação temporal no servidor (`data_hora_pedido + 24h <= data_hora_consulta`). Caso contrário, se menor que 24h, atribuição do estado "Sob Validação da IPSS". Para o fluxo básico standard (CT-01.1), >= 48h resulta em "Pendente de Triagem".

## Risks / Trade-offs

- **[Risco] Latência na validação de dados de utente e IPSS** → **[Mitigação]** Indexação otimizada de chaves estrangeiras e cache leve de perfis de elegibilidade.
- **[Risco] Conflitos de fuso horário em datas de consulta** → **[Mitigação]** Normalização de todas as datas e horas para UTC no armazenamento e validação estrita no fuso horário local de Portugal (Europe/Lisbon).
