# Economiza - Sistema de Gerenciamento Financeiro Pessoal

![Badge](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![Badge](https://img.shields.io/badge/linguagem-n%2Fa-lightgrey)
![Badge](https://img.shields.io/badge/versão-1.0-blue)

## 📝 Sobre o Projeto

O **Economiza** é um sistema projetado para auxiliar no controle e gerenciamento de finanças pessoais. A plataforma permite que os usuários cadastrem suas contas, fontes de renda, despesas e metas financeiras, oferecendo uma visão clara e consolidada da sua saúde financeira através de um dashboard interativo.

O objetivo principal é proporcionar uma ferramenta intuitiva para acompanhar o fluxo de dinheiro, desde as receitas até os gastos fixos e variáveis, além de incentivar o planejamento financeiro por meio do acompanhamento de metas e parcelamentos.

---

## 👥 Equipe de Desenvolvimento

Este projeto está sendo desenvolvido pela seguinte equipe:

* Bruna Raquel
* Eduardo Couto
* João Victor Paiva
* Ryan
* Vandré Cortês
* Zenilton Filho

---

## 📂 Estrutura do Projeto

O repositório está organizado da seguinte forma, visando a separação de responsabilidades e a facilidade de manutenção:

-   **/docs**: Contém toda a documentação de apoio do projeto, como especificações funcionais, diagramas de arquitetura e outros documentos relevantes.
-   **/tests**: Diretório dedicado aos testes automatizados do sistema, garantindo a qualidade e a estabilidade do código.
-   **README.md**: Este arquivo, que serve como guia central para o projeto.

---

## ✨ Funcionalidades

O sistema Economiza oferece um conjunto de funcionalidades para um controle financeiro completo:

### Cadastros Essenciais
-   **Contas**: Permite o cadastro de diversas contas bancárias (ex: Banco do Brasil, Nubank, carteiras digitais) para centralizar as informações.
-   **Fontes de Renda**: Registro de todas as fontes de receita do usuário (salários, freelancers, etc.).
-   **Gastos Fixos**: Cadastro de despesas recorrentes com valor fixo (aluguel, mensalidades, assinaturas).

### Gerenciamento de Parcelamentos
-   **Registro Detalhado**: Ao cadastrar uma compra parcelada, o usuário informa em qual conta o débito será realizado.
-   **Acompanhamento de Progresso**: Uma tabela exibe todos os parcelamentos, mostrando o progresso de pagamento (ex: 3/10 parcelas pagas).
-   **Status Automático**: Cada parcelamento possui uma flag de status (`Finalizado`, `Em Andamento`, `Inativo`) que é atualizada automaticamente conforme as parcelas são quitadas.

### Metas Financeiras
-   **Definição de Objetivos**: O usuário pode registrar metas financeiras, como economizar para uma viagem, comprar um bem ou criar uma reserva de emergência.
-   **Cálculo de Progresso**: O sistema calcula o progresso para alcançar cada meta.
-   **Movimentações de Metas**: Todo valor depositado para uma meta é registrado em "Movimentações Metas", servindo como base para o cálculo do progresso.

---

## 📊 Dashboard

O Dashboard é a tela principal do sistema e consolida as informações mais importantes em um só lugar, atualizando os valores em tempo real conforme as transações são realizadas.

#### **Indicadores Principais:**
-   **Soma Total de Fontes de Renda**: Apresenta o valor total das receitas cadastradas.
-   **Soma Total de Gastos Fixos**: Mostra a soma de todas as despesas fixas mensais.
-   **Total de Despesas do Mês**: Calcula o `(Total de Gastos Fixos) + (Total de Parcelamentos a Pagar no Mês)`.

#### **Cálculo do Saldo Total Atualizado:**
O saldo geral é calculado dinamicamente com a seguinte fórmula, refletindo a situação financeira real do usuário:

$$Saldo\ Total = (Total\ de\ Fontes\ de\ Renda + Transações\ de\ Entrada) - (Total\ de\ Gastos\ Fixos + Total\ de\ Parcelamentos\ a\ Pagar\ no\ Mês + Metas\ a\ Pagar\ no\ Mês)$$

As **transações de saída** são utilizadas para registrar pagamentos de gastos fixos, parcelas ou aportes em metas financeiras, mantendo o sistema sempre sincronizado.
