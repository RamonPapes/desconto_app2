# desconto_app

Sistema de pedidos de e-commerce que calcula o valor final de cada pedido aplicando descontos conforme o tipo de cliente. Projeto da disciplina **Alta Qualidade em Software** (SENAI CIMATEC).

## Funcionalidades

- Receber pedidos de clientes
- Aplicar desconto conforme o tipo (Normal 10%, VIP 20%, Premium 30%)
- Salvar os pedidos
- Listar os pedidos já registrados

## Arquitetura

### Arquitetura Limpa (atual)

As regras de negócio não dependem de banco, framework, tela ou biblioteca externa. As dependências sempre apontam para dentro, em direção às entidades.

```
src/app/
├── entities/                # Regras de negócio essenciais (Pedido, Desconto)
├── use_cases/               # Ações do sistema (CriarPedido): coordena o fluxo usando as entidades
├── gateways/                # Contratos (interfaces) que o use case precisa, ex.: IPedidoGateway
├── dtos/                    # Objetos que transportam dados entre camadas (Input/Output DTO)
├── presenters/              # Formata a saída do use case para exibição (dict)
├── adapters/
│   ├── controllers/         # Porta de entrada: recebe a requisição e chama o use case
│   └── repositories/        # Implementação concreta do gateway (MemoryPedidoRepository)
└── frameworks/database/     # Infraestrutura: banco de dados em memória
main.py                      # Monta as dependências e executa o fluxo
```

Fluxo: `Controller → InputDTO → Use Case → Gateway (Repository) → Database`, e a resposta volta como `OutputDTO → Presenter`.

### Arquitetura em Camadas (anterior)

A primeira versão do projeto, mantida em `src_antigo/` como referência.

```
src_antigo/
├── controllers/   # Recebe as entradas e encaminha para os serviços
├── services/      # Regras de negócio (cálculo de descontos, validações)
├── repositories/  # Abstrai o acesso aos dados (salvar e recuperar)
├── database/      # Infraestrutura: conexão com o banco de dados
└── models/        # Entidades do sistema (Pedido, Desconto)
```

Fluxo: `Controller → Service → Repository → Database`

## Como executar

```bash
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
python main.py
```
