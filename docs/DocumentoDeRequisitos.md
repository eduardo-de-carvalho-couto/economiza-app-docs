# Documento de Requisitos de Software (SRS): Economiza

| **Nome do Projeto** | Economiza - Sistema de Gerenciamento Financeiro Pessoal |
| :--- | :--- |
| **Versão** | 1.0 |
| **Data** | 23 de junho de 2025 |
| **Status** | Rascunho |

---

## 1. Introdução

### 1.1. Propósito
Este documento define os requisitos funcionais e não funcionais para a versão 1.0 do sistema **Economiza**. Ele serve como a principal referência para as equipes de design, desenvolvimento e testes, garantindo que o produto final atenda às especificações e às necessidades dos usuários.

### 1.2. Escopo do Produto
O sistema **Economiza** será uma aplicação web que permitirá aos usuários gerenciar suas finanças pessoais. As funcionalidades incluem o cadastro e controle de contas, rendas, gastos fixos, parcelamentos e metas financeiras. O objetivo é fornecer uma visão consolidada e clara da saúde financeira do usuário através de um dashboard interativo. Funcionalidades como integração automática com bancos (Open Finance) e gerenciamento de investimentos estão fora do escopo desta versão.

### 1.3. Definições, Acrônimos e Abreviações
* **SRS**: Software Requirements Specification (Documento de Requisitos de Software)
* **PDD**: Product Definition Document (Documento de Definição de Produto)
* **RF**: Requisito Funcional
* **RNF**: Requisito Não Funcional
* **UI**: User Interface (Interface do Usuário)
* **CRUD**: Create, Read, Update, Delete (Criar, Ler, Atualizar, Deletar)

### 1.4. Referências
* `README.md` do projeto Economiza.
* `DefiniçãoDeProduto.md` (Documento de Definição de Produto).

### 1.5. Visão Geral do Documento
Este documento está organizado da seguinte forma: A Seção 2 fornece uma descrição geral do produto. A Seção 3, o coração do documento, detalha os requisitos funcionais e não funcionais específicos do sistema.

## 2. Descrição Geral

O sistema **Economiza** é uma plataforma independente projetada para usuários que desejam maior controle sobre suas finanças. Ele substitui métodos manuais, como planilhas, por uma interface gráfica intuitiva e cálculos automatizados, visando simplificar o planejamento financeiro pessoal.

## 3. Requisitos Específicos

### 3.1. Requisitos Funcionais

A tabela a seguir detalha as funcionalidades que o sistema deve executar.

| ID | Título do Requisito | Descrição | Prioridade |
| :--- | :--- | :--- | :--- |
| **RF001** | Cadastro de Novo Usuário | O sistema deve permitir que um novo usuário se cadastre fornecendo um nome, e-mail e senha. | Alta |
| **RF002** | Autenticação de Usuário | O sistema deve permitir que um usuário cadastrado faça login utilizando seu e-mail e senha. | Alta |
| **RF003** | Cadastro de Conta | O sistema deve permitir que o usuário cadastre suas contas financeiras (ex: Banco do Brasil, Nubank), informando um nome/apelido para a conta. | Alta |
| **RF004** | Cadastro de Fonte de Renda | O sistema deve permitir que o usuário cadastre fontes de renda, especificando um nome e o valor. | Alta |
| **RF005** | Cadastro de Gasto Fixo | O sistema deve permitir que o usuário cadastre gastos fixos mensais, especificando uma descrição e o valor. | Alta |
| **RF006** | CRUD de Contas/Rendas/Gastos | O sistema deve fornecer funcionalidades para Visualizar, Editar e Excluir todos os itens cadastrados (Contas, Rendas e Gastos Fixos). | Alta |
| **RF007** | Registro de Parcelamento | O sistema deve permitir que o usuário registre uma compra parcelada, informando a descrição, o valor da parcela, a quantidade de parcelas e a qual conta o débito pertence. | Alta |
| **RF008** | Visualização de Parcelamentos | O sistema deve exibir uma lista com todos os parcelamentos, mostrando o progresso (ex: "Parcela 3/10") e um status (`Em andamento`, `Finalizado`). | Alta |
| **RF009** | Atualização de Status do Parcelamento | O status de um parcelamento deve ser atualizado para "Finalizado" automaticamente quando a última parcela for registrada como paga. | Média |
| **RF010** | Criação de Meta Financeira | O sistema deve permitir que o usuário crie uma meta financeira, definindo um nome e um valor total a ser alcançado. | Alta |
| **RF011** | Registro de Aporte em Meta | O sistema deve permitir que o usuário registre valores ("Movimentações Metas") depositados para o progresso de uma meta específica. | Alta |
| **RF012** | Cálculo de Progresso da Meta | O sistema deve calcular e exibir visualmente (ex: barra de progresso) o percentual já alcançado de cada meta. | Alta |
| **RF013** | Dashboard: Soma de Rendas | O dashboard deve exibir um somatório de todas as fontes de renda cadastradas. | Alta |
| **RF014** | Dashboard: Soma de Gastos Fixos | O dashboard deve exibir um somatório de todos os gastos fixos cadastrados. | Alta |
| **RF015** | Dashboard: Soma das Despesas do Mês | O dashboard deve exibir um somatório do total de gastos fixos mais o total de parcelamentos a pagar no mês corrente. | Alta |
| **RF016** | Dashboard: Cálculo do Saldo Total | O dashboard deve exibir o saldo total atualizado, calculado pela fórmula: `(TOTAL DE FONTES DE RENDA + TRANSAÇÕES DE ENTRADA) - (TOTAL DE GASTOS FIXOS + TOTAL DE PARCELAMENTOS A PAGAR DO MES + METAS A PAGAR DO MÊS)`. | Alta |

### 3.2. Requisitos Não Funcionais

| ID | Título do Requisito | Descrição | Prioridade |
| :--- | :--- | :--- | :--- |
| **RNF001** | Segurança | Todos os dados sensíveis do usuário, especialmente senhas, devem ser armazenados de forma criptografada no banco de dados. A comunicação entre cliente e servidor deve usar HTTPS. | Alta |
| **RNF002**| Usabilidade | A interface do usuário (UI) deve ser intuitiva, limpa e responsiva, adaptando-se a diferentes tamanhos de tela (desktops e tablets). O fluxo de navegação deve ser simples, exigindo o mínimo de cliques para realizar tarefas comuns. | Alta |
| **RNF003**| Desempenho | O tempo de carregamento do dashboard principal não deve exceder 3 segundos em uma conexão de internet padrão. As consultas e cálculos devem ser otimizados para uma resposta rápida. | Alta |
| **RNF004**| Confiabilidade | O sistema deve ter uma disponibilidade (uptime) de 99%. Todos os cálculos financeiros devem ser precisos e testados rigorosamente para evitar erros de arredondamento ou lógica. | Alta |
| **RNF005**| Compatibilidade | A aplicação web deve ser compatível com as duas versões mais recentes dos navegadores Google Chrome, Mozilla Firefox e Microsoft Edge. | Média |