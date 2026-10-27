# desconto_app

Sistema de pedidos de e-commerce que calcula o valor final de cada pedido aplicando descontos conforme o tipo de cliente. Projeto da disciplina **Alta Qualidade em Software** (SENAI CIMATEC).

## Funcionalidades

- Receber pedidos de clientes
- Aplicar desconto conforme o tipo (Normal 10%, VIP 20%, Premium 30%)
- Salvar os pedidos
- Listar os pedidos já registrados

## Arquitetura

```
src/
├── controllers/   # Recebe as entradas e encaminha para os serviços
├── services/      # Regras de negócio (cálculo de descontos, validações)
├── repositories/  # Abstrai o acesso aos dados (salvar e recuperar)
├── database/      # Infraestrutura: conexão com o banco de dados
└── models/        # Entidades do sistema (Pedido, Desconto)
main.py            # Ponto de entrada da aplicação
```

Fluxo: `Controller → Service → Repository → Database`

## Como executar

```bash
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
python main.py
```
