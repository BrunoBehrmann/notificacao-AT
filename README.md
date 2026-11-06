# ✉️ Microsserviço de Notificação

> API dedicada ao disparo e gerenciamento de notificações por e-mail automatizadas.

---

## 🎯 Sobre o Projeto

O microsserviço **notificacao** é responsável por consumir eventos/chamadas de tarefas agendadas e realizar a montagem e envio dos e-mails de alerta aos usuários. Ele garante que a camada de comunicação esteja totalmente desassociada das regras de agendamento e cadastro.

---

## 🏛️ Arquitetura do Ecossistema

O sistema completo é composto por 4 microsserviços independentes e containerizados com **Docker**:

1. **[bff-agendador-tarefas](https://github.com/BrunoBehrmann/bff-agendador-tarefas)**: Gateway / BFF que recebe as chamadas externas e orquestra os fluxos.
2. **[agendador-tarefas](https://github.com/BrunoBehrmann/agendador-tarefas)**: Microsserviço responsável pelas regras de agendamento, persistência e execução temporizada (Cron/Task).
3. **[usuario](https://github.com/BrunoBehrmann/usuario)**: Microsserviço de gestão, cadastro e validação dos dados de usuários.
4. **[notificacao](https://github.com/BrunoBehrmann/notificacao)** *(Repositório Atual)*: Microsserviço dedicado ao disparo automatizado de e-mails e alertas.

---

## 🛠️ Tecnologias e Dependências

* **Core & Framework:**
  * **Java 17+**
  * **Spring Boot**
  * **Spring Boot Starter Mail** (Integração e envio de e-mails via SMTP)
  * **Spring Web**
* **DevOps & Build:**
  * **Docker**
  * **Maven**

---

## 📌 Endpoints Internos

| Método | Endpoint | Descrição |
| :--- | :--- | :--- |
| `POST` | `/notificacao` | Recebe a solicitação e dispara o e-mail cadastrado |
