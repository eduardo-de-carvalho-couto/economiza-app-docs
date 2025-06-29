
#### Contas e Transações

**Responsável pelo gerenciamento de contas bancárias e movimentações financeiras. As contas podem ser de diferentes tipos (corrente, poupança, cartão) e cada transação está vinculada a uma conta específica. Este contexto forma a base operacional do sistema, registrando todas as movimentações financeiras dos usuários. Implementa scopes para facilitar consultas específicas por tipo de conta.**

```mermaid
classDiagram
    class Model {
        <<Laravel Base Class>>
    }

    class User {
        +id
    }

    class Conta {
        +user(): BelongsTo
        +getTipos(): array$
        +getTipoLabelAttribute(): string
        +getStatusAttribute(): string
        +scopeAtivas()
        +scopeCartoesCredito()
        +scopeContasBancarias()
    }

    class Transacao {
        +usuario(): BelongsTo
        +conta(): BelongsTo
    }

    class HasFactory {
        <<trait>>
    }
    class SoftDeletes {
        <<trait>>
    }

    Model <|-- Conta
    Model <|-- Transacao

    User "1" --> "0..*" Conta : possui
    User "1" --> "0..*" Transacao : realiza
    Conta "1" --> "0..*" Transacao : contém

    HasFactory ..> Conta : uses
    HasFactory ..> Transacao : uses
    SoftDeletes ..> Conta : uses
    SoftDeletes ..> Transacao : uses
```

#### Gastos e Receitas

**Gerencia as fontes de renda e gastos fixos dos usuários. FonteRenda registra todas as entradas financeiras recorrentes, enquanto GastoFixo controla despesas regulares vinculadas a contas específicas. Este contexto é essencial para o planejamento financeiro, permitindo que usuários tenham visibilidade sobre seus fluxos de entrada e saída previsíveis. Ambas as classes suportam soft delete para histórico.**

```mermaid
classDiagram
    class Model {
        <<Laravel Base Class>>
    }

    class User {
        +id
    }

    class Conta {
        +id
    }

    class FonteRenda {
        +usuario(): BelongsTo
    }

    class GastoFixo {
        +usuario(): BelongsTo
        +conta(): BelongsTo
    }

    class SoftDeletes {
        <<trait>>
    }

    Model <|-- FonteRenda
    Model <|-- GastoFixo

    User "1" --> "0..*" FonteRenda : possui
    User "1" --> "0..*" GastoFixo : cadastra
    Conta "1" --> "0..*" GastoFixo : vincula

    SoftDeletes ..> FonteRenda : uses
    SoftDeletes ..> GastoFixo : uses
```

#### Metas Financeiras

**Sistema completo de definição e acompanhamento de objetivos financeiros. MetaFinanceira permite aos usuários estabelecer metas com prazos e valores, enquanto MovimentacaoMeta registra todos os depósitos e retiradas. Inclui cálculos automatizados de progresso, dias restantes e status. Este é o contexto mais rico em regras de negócio, fornecendo insights detalhados sobre o progresso das metas através de múltiplos accessors e scopes.**

```mermaid
classDiagram
    class Model {
        <<Laravel Base Class>>
    }

    class User {
        +id
    }

    class Transacao {
        +id
    }

    class MetaFinanceira {
        +usuario(): BelongsTo
        +movimentacoes(): HasMany
        +getValorAtualAttribute(): float
        +getProgressoAttribute(): float
        +getProgressoStatusAttribute(): string
        +getValorRestanteAttribute(): float
        +getDiasRestantesAttribute(): int
        +getDiasDecorridosAttribute(): int
        +getStatusBadgeColorAttribute(): string
        +getCategoriaBadgeColorAttribute(): string
        +getCategoriaLabelAttribute(): string
        +getStatusLabelAttribute(): string
        +scopeAtivas()
        +scopePorCategoria()
        +scopePorUsuario()
        +scopeConcluidas()
        +scopeVencendo()
        +scopeVencidas()
    }

    class MovimentacaoMeta {
        +meta(): BelongsTo
        +transacao(): BelongsTo
        +getTipoBadgeColorAttribute(): string
        +getTipoLabelAttribute(): string
        +getValorFormatadoAttribute(): string
        +scopeDepositos()
        +scopeRetiradas()
        +scopePorMeta()
        +scopePorPeriodo()
    }

    class HasFactory {
        <<trait>>
    }
    class SoftDeletes {
        <<trait>>
    }

    Model <|-- MetaFinanceira
    Model <|-- MovimentacaoMeta

    User "1" --> "0..*" MetaFinanceira : define
    MetaFinanceira "1" --> "0..*" MovimentacaoMeta : contém
    Transacao "0..1" --> "0..1" MovimentacaoMeta : gera

    HasFactory ..> MetaFinanceira : uses
    HasFactory ..> MovimentacaoMeta : uses
    SoftDeletes ..> MetaFinanceira : uses
    SoftDeletes ..> MovimentacaoMeta : uses
```

#### Parcelamentos

**Controla compras e gastos parcelados dos usuários. A classe Parcelamento gerencia informações como valor total, número de parcelas e progresso de pagamento. O ParcelamentoObserver implementa o padrão Observer, automatizando cálculos e validações em tempo real. Este contexto é fundamental para o controle de compromissos financeiros futuros, oferecendo visibilidade completa sobre parcelas pendentes e quitadas.**

```mermaid
classDiagram
    class Model {
        <<Laravel Base Class>>
    }

    class User {
        +id
    }

    class Conta {
        +id
    }

    class Parcelamento {
        +usuario(): BelongsTo
        +conta(): BelongsTo
        +getStatusAttribute(): string
        +getProgressoAttribute(): float
        +getValorRestanteAttribute(): float
        +scopeAtivos()
        +scopePorUsuario()
        +scopeEmAndamento()
        +scopeFinalizados()
    }

    class ParcelamentoObserver {
        +creating(Parcelamento): void
        +created(Parcelamento): void
        +updating(Parcelamento): void
        +updated(Parcelamento): void
        +deleted(Parcelamento): void
        +restored(Parcelamento): void
        +forceDeleted(Parcelamento): void
    }

    class HasFactory {
        <<trait>>
    }
    class SoftDeletes {
        <<trait>>
    }

    Model <|-- Parcelamento

    User "1" --> "0..*" Parcelamento : possui
    Conta "1" --> "0..*" Parcelamento : vincula
    ParcelamentoObserver "1" ..> "1" Parcelamento : observes

    HasFactory ..> Parcelamento : uses
    SoftDeletes ..> Parcelamento : uses
```
