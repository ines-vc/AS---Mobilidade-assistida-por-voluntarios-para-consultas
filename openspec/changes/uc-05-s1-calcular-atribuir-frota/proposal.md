# Proposal: UC-05.S1 - Calcular e Atribuir Frota ou Voluntário (Matching Inteligente)

## Why

Atualmente, após a submissão de pedidos de transporte assistido no estado "Pendente de Triagem", a afetação manual de condutores voluntários ou viaturas adaptadas de parceiros (Câmara Municipal / Bombeiros) consome tempo e recursos operacionais significativos da IPSS. O Slice UC-05.S1 implementa o algoritmo de matching inteligente (UC-05, Fluxo Básico) que cruza automaticamente o perfil e necessidades de mobilidade do utente (mobilidade ligeira, deficiência visual, cadeira de rodas) com a disponibilidade e características dos condutores voluntários e viaturas adaptadas, otimizando rotas e alocando o recurso adequado em menos de 5 segundos (RNF-021).

## What Changes

- **Algoritmo de Matching Inteligente**: Introdução do motor de cálculo e triagem automática para pedidos "Pendente de Triagem" (UC-05).
- **Cruzamento de Requisitos de Mobilidade**: Validação e correspondência entre o grau de mobilidade do utente (ligeira, moderada, severa/cadeira de rodas) e os atributos do recurso (viatura ligeira de voluntário vs. viatura adaptada de parceiro, conforme BR-02).
- **Atribuição Automática e Reserva de Recurso**: Seleção do voluntário/veículo com maior pontuação de alinhamento e otimização de rota, reserva do recurso, notificação do condutor/parceiro e atualização do estado do pedido para "Atribuído".
- **Fluxo Alternativo de Afetação Adaptada (A1)**: Priorização automática de carrinhas adaptadas para utentes com dependência de cadeira de rodas não dobrável.

## Capabilities

### New Capabilities
- (Nenhuma - utilizando a capacidade existente `transporte-assistido`)

### Modified Capabilities
- `transporte-assistido`: Adição de requisitos para o cálculo automático e atribuição de frota e voluntários com base nas necessidades de mobilidade (UC-05).

## Impact

- **Módulos / Componentes**: Motor de Regras e Atribuição (Backend Service), Módulo de Gestão de Frota e Voluntários, Serviço de Notificações.
- **APIs / Base de Dados**: Extensão do modelo de dados para `MissaoTransporte`/`Atribuicao`, horários e disponibilidades de `Voluntario` e `ViaturaAdaptada`, e registo de pontuações de matching.
- **Dependências**: Integração com API Google Maps (para otimização de rotas e proximidade) e serviço de notificações push/SMS.
