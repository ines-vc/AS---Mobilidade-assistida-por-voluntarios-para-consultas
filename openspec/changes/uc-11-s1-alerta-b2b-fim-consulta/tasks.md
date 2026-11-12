# Tasks: UC-11.S1 - Receber Alerta B2B de Fim de Consulta

## 1. Modelo de Dados e Segurança B2B
- [ ] 1.1 Criar entidade `CredencialHospitalB2B` para autenticação das unidades de saúde parceiras.
- [ ] 1.2 Criar tabela de auditoria `EventoHospitalarB2B` (`referencia_missao`, `tipo_evento`, `recebido_em`).

## 2. Lógica de Negócio e API (Backend)
- [ ] 2.1 Implementar middleware de autenticação para o endpoint B2B hospitalar.
- [ ] 2.2 Implementar handler `POST /api/b2b/hospital/eventos` para processar `ENTRADA_CONSULTA` e `FIM_CONSULTA`, atualizando o estado para `"Pronto para Recolha"`.
- [ ] 2.3 Integrar serviço de envio de notificação imediata para o voluntário/frota atribuída[cite: 7, 8].

## 3. Testes de Aceitação
- [ ] 3.1 Implementar teste automatizado para **CT-11.1** (receção de `FIM_CONSULTA` válido, mudança de estado e disparo de notificação)[cite: 9, 11].
- [ ] 3.2 Implementar teste automatizado para **CT-11.2** (rejeição HTTP 401 para pedidos B2B sem credenciais válidas).
