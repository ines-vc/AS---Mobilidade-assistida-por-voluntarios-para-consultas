# Tasks: UC-05.S1 - Calcular e Atribuir Frota ou Voluntário

## 1. Modelo de Dados e Persistência
- [ ] 1.1 Adicionar atributos de requisitos de mobilidade (`tipo_mobilidade`, `requer_viatura_adaptada`, `requer_acompanhamento`) ao modelo `PedidoTransporte`.
- [ ] 1.2 Criar entidades/relações para `RecursoFrota` (`Voluntario` e `ViaturaAdaptadaParceiro`) e respetivas janelas de disponibilidade.

## 2. Lógica de Negócio (Backend)
- [ ] 2.1 Implementar filtro de elegibilidade técnica (separação entre viatura ligeira e viatura adaptada com rampa/elevador).
- [ ] 2.2 Implementar verificação de disponibilidade temporal (janela de ida e regresso estimada) e bloqueio transacional do recurso selecionado.
- [ ] 2.3 Expor endpoint interno/API para acionar o cálculo de matching e persistir a transição de estado para `"Atribuído"`.

## 3. Testes de Aceitação
- [ ] 3.1 Implementar teste automatizado para **CT-05.1** (atribuição de voluntário com viatura ligeira para utente com mobilidade ligeira/deficiência visual).
- [ ] 3.2 Implementar teste automatizado para **CT-05.2** (exclusão de carro ligeiro e alocação de viatura adaptada de parceiro para utente em cadeira de rodas pesada).
