# Documento de Definição de Produto (PDD): Economiza

| **Nome do Projeto** | Economiza - Sistema de Gerenciamento Financeiro Pessoal |
| :--- | :--- |
| **Versão** | 1.0 |
| **Data** | 27 de junho de 2025 |
| **Equipe** | Bruna Raquel, Eduardo Couto, João Victor Paiva, Ryan, Vandré Cortês, Zenilton Filho |

### 1. Visão Geral (Resumo Executivo)

O **Economiza** é uma aplicação de gerenciamento financeiro pessoal projetada para oferecer aos usuários uma visão clara e centralizada de sua saúde financeira. Em um cenário onde o controle financeiro é muitas vezes fragmentado e complexo, o Economiza surge como uma solução intuitiva que permite o registro de contas, rendas e despesas, o acompanhamento de compras parceladas e a definição de metas de economia. Através de um dashboard consolidado, o produto visa capacitar os usuários a tomar decisões financeiras mais inteligentes, reduzir o estresse financeiro e atingir seus objetivos de longo prazo.

### 2. O Problema (O "Porquê")

Muitas pessoas enfrentam dificuldades significativas para gerenciar suas finanças pessoais, resultando em endividamento, estresse e incapacidade de poupar. Os principais problemas que o Economiza se propõe a resolver são:

* **Falta de Visibilidade:** As informações financeiras estão espalhadas por múltiplas contas bancárias, cartões de crédito e planilhas, dificultando a obtenção de uma visão completa das finanças.
* **Controle Manual e Ineficiente:** O uso de planilhas ou cadernos é propenso a erros, demorado e não oferece insights dinâmicos sobre os hábitos de consumo.
* **Dificuldade em Acompanhar Dívidas:** O controle de múltiplas compras parceladas, suas datas de vencimento e o progresso do pagamento é uma tarefa complexa e fácil de se perder.
* **Falta de Planejamento e Motivação:** Sem metas claras e um acompanhamento do progresso, muitos desistem de seus objetivos de economia por não verem resultados tangíveis.

### 3. A Solução (O "O Quê")

O Economiza resolverá esses problemas fornecendo uma **plataforma centralizada, simples e visual** onde o usuário pode:

1.  **Consolidar** todas as suas informações financeiras em um único lugar.
2.  **Automatizar** o cálculo de balanços mensais e totais.
3.  **Visualizar** claramente o progresso de pagamento de dívidas e o avanço em direção a metas financeiras.
4.  **Obter insights** rápidos através de um dashboard interativo que resume sua posição financeira atual.

### 4. Objetivos do Produto e Métricas de Sucesso

#### 4.1. Objetivos para o Usuário
* **Clareza Financeira:** Proporcionar uma visão clara e descomplicada de para onde o dinheiro está indo.
* **Capacitação:** Dar ao usuário as ferramentas necessárias para planejar, controlar e atingir metas financeiras.
* **Redução de Estresse:** Diminuir a ansiedade relacionada às finanças ao simplificar o gerenciamento de dívidas e despesas.

#### 4.2. Objetivos para o Projeto (Metas de Negócio)
* **Validação do Conceito:** Entregar um Produto Mínimo Viável (MVP) que resolva os problemas centrais do público-alvo.
* **Engajamento:** Manter os usuários ativos na plataforma, incentivando o registro contínuo de suas finanças.
* **Base Sólida:** Construir uma arquitetura escalável que permita a adição de novas funcionalidades no futuro.

#### 4.3. Métricas de Sucesso (KPIs)
* **Aquisição:** Número de cadastros na plataforma.
* **Ativação:** Percentual de usuários que completam os cadastros iniciais (pelo menos uma conta, uma renda e um gasto).
* **Retenção:** Percentual de usuários que retornam à plataforma semanalmente/mensalmente.
* **Adoção de Funcionalidades:** Número de metas e parcelamentos criados por usuário.
* **Feedback Qualitativo:** Coleta de avaliações e sugestões dos usuários para guiar melhorias.

### 5. Público-Alvo

* **Jovens Adultos e Universitários:** Indivíduos que estão começando a vida financeira e precisam criar hábitos saudáveis de controle de gastos.
* **Profissionais em Início de Carreira:** Pessoas com renda fixa que buscam organizar suas despesas, quitar dívidas (como financiamentos) e começar a poupar para objetivos maiores.
* **Qualquer pessoa** que atualmente utiliza métodos manuais (planilhas, cadernos) e busca uma solução mais prática e automatizada.

### 6. Funcionalidades Detalhadas (Escopo da Versão 1.0)

#### 6.1. Módulo de Cadastros
-   **Gerenciamento de Contas:**
    -   [ ] O usuário pode adicionar múltiplas contas (corrente, poupança, carteira digital).
    -   [ ] O usuário pode editar e remover contas existentes.
-   **Gerenciamento de Fontes de Renda:**
    -   [ ] O usuário pode cadastrar suas fontes de renda com nome e valor.
-   **Gerenciamento de Gastos Fixos:**
    -   [ ] O usuário pode cadastrar despesas mensais recorrentes (aluguel, internet, etc.).

#### 6.2. Módulo de Parcelamentos
-   [ ] O usuário pode registrar uma nova compra parcelada, associando-a a uma conta específica.
-   [ ] O sistema deve exibir uma lista de todos os parcelamentos com as seguintes informações: descrição, valor da parcela, progresso (ex: "3/12") e valor total.
-   [ ] O sistema deve atualizar automaticamente o status do parcelamento para `Em Andamento`, `Finalizado` ou `Inativo` com base nos pagamentos registrados.

#### 6.3. Módulo de Metas Financeiras
-   [ ] O usuário pode criar metas financeiras (ex: "Viagem para a praia", "Reserva de Emergência") com um valor-alvo.
-   [ ] O usuário pode registrar aportes ("Movimentações Metas") para cada meta.
-   [ ] O sistema deve calcular e exibir o progresso percentual para atingir a meta.

#### 6.4. Dashboard Principal
-   [ ] Exibir um card com o somatório de todas as fontes de renda.
-   [ ] Exibir um card com o somatório de todos os gastos fixos.
-   [ ] Exibir um card com o somatório das despesas do mês (Gastos Fixos + Parcelas do mês).
-   [ ] Exibir um card principal com o **Saldo Total**, calculado pela fórmula:
    $$Saldo = (Rendas + Entradas) - (Gastos Fixos + Parcelas do Mês + Aportes em Metas)$$
-   [ ] O dashboard deve ser a tela inicial e refletir todas as transações em tempo real.

### 7. Jornada do Usuário (Exemplo de Uso)

João, um jovem profissional, se cadastra no Economiza. Primeiro, ele adiciona sua conta do "Nu Bank" e sua carteira do "Banco do Brasil". Em seguida, ele cadastra seu salário como fonte de renda e suas despesas fixas: aluguel e internet. João comprou um celular novo e lança o parcelamento de 10x de R$ 300, associando a despesa à sua conta do Nu Bank. Ele também cria uma meta de "Juntar R$ 5.000 para uma viagem". No fim do mês, ao receber o salário, ele registra um aporte de R$ 400 para sua meta. Ao acessar o dashboard, ele vê seu saldo atualizado, o progresso da sua meta e que ainda faltam 9 parcelas do celular a serem pagas.

### 8. Requisitos Não Funcionais

* **Usabilidade:** A interface deve ser limpa, intuitiva e fácil de usar, mesmo para usuários com pouca afinidade tecnológica.
* **Segurança:** Os dados financeiros dos usuários são sensíveis e devem ser armazenados de forma segura, com práticas adequadas de proteção de dados.
* **Desempenho:** O dashboard e os cálculos devem ser processados rapidamente para não frustrar o usuário.
* **Confiabilidade:** O sistema deve ser estável e os cálculos financeiros, precisos e sem erros.

### 9. Fora do Escopo (Considerações para o Futuro)

As seguintes funcionalidades **não** farão parte da versão 1.0, mas poderão ser consideradas para versões futuras:

* Importação automática de extratos bancários (Open Finance).
* Gerenciamento de investimentos (ações, fundos imobiliários, etc.).
* Controle de orçamento por categorias (alimentação, transporte, lazer).
* Geração de relatórios gráficos avançados.
* Suporte a múltiplas moedas.
* Aplicativo móvel (iOS/Android).