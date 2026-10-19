# 📄 Documentação de Requisitos e Modelagem (Momento 2 feito embaixo)

## 1. USER STORIES (INVEST)

- **US01:** "Como técnico, quero abrir uma Ordem de Serviço para registrar um conserto."
  - **C.A.01:** Deve validar o ID do cliente.
  - **C.A.02:** O status inicial deve ser sempre `'ABERTA'`.
- **US02:** "Como cliente, quero visualizar o status do meu equipamento."

---

## 2. REQUISITOS NÃO-FUNCIONAIS (RNF)

- **RNF01 (Segurança):** Sanitização de inputs contra XSS/OWASP no cadastro.
- **RNF02 (Desempenho):** Tempo de resposta na criação de chamados < 2s.

---

## 3. DIAGRAMA DE CLASSES (POO)

```mermaid
classDiagram
    class Usuario {
        <<Abstract>>
        -int id
        -string nome
        -string email
        +getId()
        +getNome()
        +getEmail()
    }

    class Cliente {
        -string telefone
    }

    class Tecnico {
        -string especialidade
    }

    class OrdemServico {
        -int id
        -Cliente cliente
        -string status
    }

    Usuario <|-- Cliente : Herança
    Usuario <|-- Tecnico : Herança
    Cliente "1" -- "*" OrdemServico : solicita
    Tecnico "1" -- "*" OrdemServico : atende
