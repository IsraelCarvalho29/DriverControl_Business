`mermaid`
erDiagram

    EMPRESA {
        int id PK
        string nome
        string cnpj
        string telefone
        string email
        string endereco
        datetime criado_em
    }

    MOTORISTA {
        int id PK
        string nome
        string cpf
        string cnh
        string telefone
        string email
        string endereco
        string status
        datetime criado_em
    }

    VEICULO {
        int id PK
        string placa
        string modelo
        string marca
        int ano
        string cor
        string renavam
        string status
        datetime criado_em
    }

    CONTRATO {
        int id PK
        int motorista_id FK
        int veiculo_id FK
        date data_inicio
        date data_fim
        decimal valor_semanal
        string status
        datetime criado_em
    }

    PAGAMENTO {
        int id PK
        int contrato_id FK
        decimal valor
        string metodo
        date data_pagamento
        string status
        datetime criado_em
    }

    MANUTENCAO {
        int id PK
        int veiculo_id FK
        string tipo
        string descricao
        decimal custo
        date data_manutencao
        datetime criado_em
    }

    MULTA {
        int id PK
        int veiculo_id FK
        int motorista_id FK
        string descricao
        decimal valor
        date data_multa
        string status
        datetime criado_em
    }

    EMPRESA ||--o{ VEICULO : possui
    MOTORISTA ||--o{ CONTRATO : assina
    VEICULO ||--o{ CONTRATO : alugado_em
    CONTRATO ||--o{ PAGAMENTO : gera
    VEICULO ||--o{ MANUTENCAO : recebe
    VEICULO ||--o{ MULTA : possui
    MOTORISTA ||--o{ MULTA : recebe
