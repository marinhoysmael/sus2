### 5. Sistema de Reserva de Consultas Médicas
**Descrição:** Plataforma para agendar consultas e exames.

**Requisitos Funcionais:**
1. Cadastro de médicos e especialidades.
2. Agendamento de consultas.
3. Cancelamento e reagendamento.
4. Notificações automáticas.

**Requisitos Não Funcionais:**
- Interface intuitiva.
- Disponível 24/7.

**Histórias de Usuário:**
- **Como paciente**, quero agendar consultas **para que** possa garantir atendimento.
  - **Critérios de Aceite:** Não permitir sobreposição; confirmação imediata.

**Etapas/Sprints:**
- Sprint 1: Cadastro de médicos.
- Sprint 2: Agendamentos.
- Sprint 3: Notificações.
------------------------------------------------------------------------
**Entidades:**

-   **Medico**
    -   `id` (PK)\
    -   `nome`\
    -   `crm` (único, regex CRM: `^\d{6}-[A-Z]{2}$`)\
    -   `especialidade`
-   **Paciente**
    -   `id` (PK)\
    -   `nome`\
    -   `email` (único)\
    -   `telefone`
-   **Consulta**
    -   `id` (PK)\
    -   `medico_id` (FK → Medico)\
    -   `paciente_id` (FK → Paciente)\
    -   `data_hora` (obrigatório)\
    -   `status` (enum: `AGENDADA`, `CANCELADA`, `REALIZADA`)\
    -   **Regra:** Não permitir duas consultas no mesmo horário para o
        mesmo médico.
