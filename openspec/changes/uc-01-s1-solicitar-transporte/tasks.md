# Tasks: UC-01.S1 - Solicitar Transporte Assistido

## 1. Backend e Modelo de Dados

- [ ] 1.1 Criar entidade/modelo de dados para `PedidoTransporte` e validação de vínculo de elegibilidade com `IPSSParceira` (BR-03), verificando via testes unitários de modelo.
- [ ] 1.2 Implementar serviço de validação da antecedência mínima de agendamento (24h) (BR-01) e cálculo do estado inicial "Pendente de Triagem", verificando via testes unitários de regra de negócio.

## 2. API e Lógica de Submissão

- [ ] 2.1 Desenvolver endpoint REST de submissão de pedido de transporte assistido com resposta em < 2s (RNF-02), integrando validação de elegibilidade e antecedência.
- [ ] 2.2 Implementar tratamento de erro e recusa com mensagem informativa quando o utente não possui elegibilidade social ativa (CT-01.3), verificando via testes de integração da API.

## 3. Frontend (Portal Web e App Móvel) e Testes de Aceitação

- [ ] 3.1 Desenvolver ecrã/formulário de submissão de pedido de transporte (recolha, destino, data/hora, condicionantes de mobilidade) respeitando acessibilidade sénior (WCAG 2.1 AA).
- [ ] 3.2 Implementar fluxo de submissão bem-sucedida com agendamento a 48h resultando em estado "Pendente de Triagem" e notificação de confirmação (CT-01.1), verificando via testes de aceitação End-to-End.

## Workflow follow-up

- Arquivar a change após revisão e aprovação dos artefactos e testes.
