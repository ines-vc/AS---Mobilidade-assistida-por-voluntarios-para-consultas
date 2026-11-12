# Tasks: UC-08.S1 - Realizar Missão de Transporte

## 1. Modelo de Dados e Persistência
- [ ] 1.1 Criar/atualizar tabela `ExecucaoMissao` com os estados da viagem e timestamps (`recolha_em`, `chegada_hospital_em`, `inicio_regresso_em`, `concluida_em`).
- [ ] 1.2 Criar tabela `MovimentoBancoTempo` com referência única à missão (`missao_id`) e saldo acumulado do voluntário[cite: 5, 8].

## 2. Lógica de Negócio (Backend)
- [ ] 2.1 Implementar máquina de estados da missão com validação de transições sequenciais.
- [ ] 2.2 Implementar listener/serviço de cálculo de duração e crédito automático no Banco de Tempo ao atingir o estado `"Concluído"`[cite: 5, 8].
- [ ] 2.3 Criar endpoints REST para registo das etapas da missão pela App Móvel[cite: 6].

## 3. Testes de Aceitação
- [ ] 3.1 Implementar teste automatizado para **CT-08.1** (transição completa das etapas da viagem até `"Concluído"`).
- [ ] 3.2 Implementar teste automatizado para **CT-08.2** (crédito correto e idempotente de horas no Banco de Tempo após conclusão)[cite: 5, 8].
