# 📋 Board Management System (Kanban Style)

Projeto Java voltado à gestão de tarefas em quadros do tipo Kanban, com funcionalidades robustas de manipulação de colunas, cartões, bloqueios, histórico e menu interativo via console.

---

## 🚀 Funcionalidades

- ✅ Criar quadros e colunas (To Do, Doing, Done, etc.)
- ✅ Adicionar cartões às colunas
- 🔁 Mover cartões entre colunas com regras de bloqueio
- 🚫 Tratar exceções específicas de fluxo (ex: cartões bloqueados ou finalizados)
- 🧠 Menu interativo para operações (UI)
- 📦 Controle de histórico de cartões
- 📄 Camadas bem definidas: DTO, DAO, Services, Entities

---

## 🧱 Estrutura do Projeto (MVC Avançado)

```
src/main/java/br/com/dio/
│
├── controller/               # Controladores principais (BoardController)
├── dto/                      # Objetos de transferência de dados (DTOs)
├── entity/                   # Entidades do domínio: Board, Column, Card, Block
├── exception/                # Exceções personalizadas
├── persistence/              # DAO, configurações, entidades persistentes
│   ├── config/               # Configuração do banco
│   ├── converter/            # Conversores de tipo (ex: datas)
│   ├── dao/                  # Objetos de acesso a dados
│   ├── entity/               # Entidades JPA
│   └── migration/            # Estratégias de migração (Liquibase)
├── service/                  # Lógica de negócio (CRUD, regras, queries)
├── ui/                       # Menu principal e de quadros (interação CLI)
└── Main.java                 # Ponto de entrada da aplicação
```

---

## 📌 Pacotes e Classes Importantes

### 🎯 UI
- `MainMenu.java` — Menu principal de operações
- `BoardMenu.java` — Interface de manipulação de quadros

### 📦 Entidades
- `BoardEntity`, `BoardColumnEntity`, `CardEntity`, `BlockEntity`

### 💼 Services
- `BoardService`, `CardService` — Lógica principal
- `BoardQueryService`, `CardQueryService`, `BoardColumnQueryService` — Consultas especializadas

### 🧰 DAO
- `BoardDAO`, `BoardColumnDAO`, `CardDAO`, `BlockDAO`

### 📄 DTOs
- `BoardDetailsDTO`, `BoardColumnDTO`, `BoardColumnInfoDTO`, `CardDetailsDTO`

### 🚨 Exceções
- `CardBlockedException`, `CardFinishedException`, `EntityNotFoundException`

### ⚙️ Outras Classes
- `MigrationStrategy` — Executa migração inicial
- `ConnectionConfig` — Configuração do banco de dados
- `OffsetDateTimeConverter` — Conversão de datas

---

## 🔄 Diagrama Mermaid (Arquitetura e Fluxo)

```mermaid
graph TD
  A[Usuário] -->|interage com| UI[Interface de Usuário]
  UI -->|chama| MainMenu[MainMenu]
  UI -->|navega para| BoardMenu[BoardMenu]

  MainMenu --> Main[Main.java]
  BoardMenu -->|operações| Controller

  Controller -->|usa serviços| Service
  Service -->|acessa dados| DAO
  DAO -->|persiste| Entity
  Service --> DTO
  DTO -->|leva dados| UI

  subgraph "Entities"
    Entity1[BoardEntity]
    Entity2[BoardColumnEntity]
    Entity3[CardEntity]
    Entity4[BlockEntity]
  end

  subgraph "Services"
    Service1[BoardService]
    Service2[CardService]
    Service3[BoardQueryService]
    Service4[CardQueryService]
    Service5[BoardColumnQueryService]
  end

  subgraph "DAOs"
    DAO1[BoardDAO]
    DAO2[BoardColumnDAO]
    DAO3[CardDAO]
    DAO4[BlockDAO]
  end

  subgraph "Exceções"
    E1[CardBlockedException]
    E2[CardFinishedException]
    E3[EntityNotFoundException]
  end

  subgraph "DTOs"
    DTO1[BoardDetailsDTO]
    DTO2[BoardColumnDTO]
    DTO3[BoardColumnInfoDTO]
    DTO4[CardDetailsDTO]
  end

  subgraph "Outros"
    O1[MigrationStrategy]
    O2[ConnectionConfig]
    O3[OffsetDateTimeConverter]
  end

  Controller --> Service
  Service --> DAO
  DAO --> Entity
  Service --> DTO
  UI --> Controller
```

---

Criado por Álvaro Silva

