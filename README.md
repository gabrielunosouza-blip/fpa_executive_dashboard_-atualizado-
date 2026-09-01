# FP&A Executive Dashboard & Data Pipeline

Projeto prático de Planejamento e Análise Financeira (FP&A) focado em acompanhar a performance real (Actual) versus o planejado (Budget), além de analisar margens operacionais, custos e variações por departamento e região.

---

## Tecnologias Utilizadas

* **PostgreSQL:** Modelagem do banco relacional em esquema estrela (Star Schema), automação de cálculos via Triggers/PL-pgSQL, e uso de Window Functions (LAG, Rolling Averages) em Views analíticas para consolidação da DRE e análise temporal.
* **Microsoft Excel:** Dashboard executivo dinâmico com filtros interativos (Slicers) e tabelas dinâmicas.
* **Power BI:** Painel executivo estruturado em 4 visões de navegação (Visão Geral, DRE Executiva, Análise de Variação e Gestão de OpEx) para acompanhamento de KPIs e tendências.

---

## Principais Métricas e KPIs (2026)

* **Receita Realizada:** R$ 74,30 Mi
* **Variação vs. Orçamento:** -3,19% (desvio de receita)
* **Lucro Bruto:** R$ 24,59 Mi
* **Margem Bruta:** 33,09%
* **Lucro Operacional:** R$ 22,59 Mi

---

## Estrutura do Banco de Dados e Automação (SQL)

O banco foi construído em PostgreSQL dividindo as informações em tabelas fato e dimensão:

* **Tabelas Dimensão:** `dimcustomer` (Clientes e Regiões), `dimproduct` (Produtos e Categorias), `dimdate` (Calendário).
* **Tabelas Fato:** `factsales` (Vendas), `factexpenses` (Despesas Operacionais), `factbudget` (Orçamento).
* **Automação (Triggers):** Regras de negócio em nível de banco de dados para cálculo automático de Receita, Custo e Lucro Bruto na inserção ou atualização de registros.
* **Views Analíticas:**
  * `vw_sales_analysis`: Consolida vendas, produtos e margem bruta percentual por transação.
  * `vw_expenses_analysis`: Agrupa despesas por departamento e centro de custo.
  * `vw_budget_vs_actual`: Une vendas e despesas ao orçamento mensal para calcular a variação percentual da receita e o lucro operacional final.
  * `vw_monthly_financial_summary`: Aplica Window Functions para cálculo de média móvel de 3 meses e variação mês a mês (MoM).

---

## Arquitetura do Dashboard (Power BI)

O relatório no Power BI foi organizado em 4 páginas focadas na jornada de análise executiva:

1. **Visão Geral:** Indicadores C-Level de resultado acumulado, variação de receita e distribuição por região e categoria.
2. **DRE Executiva (P&L):** Estruturação do resultado financeiro (Receita Líquida, CMV, Lucro Bruto, OpEx e Lucro Operacional) e evolução histórica.
3. **Análise de Variação (Budget vs Actual):** Detalhamento dos desvios operacionais entre o planejado e o realizado.
4. **Gestão de OpEx:** Acompanhamento analítico de despesas por departamento e categoria de custo.

---

## Arquivos Disponíveis no Repositório

* `fpa_pipeline_analysis.sql`: Script com a criação de tabelas, triggers, chaves e views analíticas.
* `fpa_executive_dashboard.xlsx`: Painel em Excel com dashboards e filtros.
* `fpa_dashboard.pbix`: Arquivo do Power BI com o modelo relacional e as 4 visões executivas.

---

Desenvolvido por Gabriel Henrique de Souza Cardoso como projeto de portfólio para Finanças / FP&A. 
LinkedIn: www.linkedin.com/in/gabriel-henrique-de-souza-cardoso-9aa9b7217

*Projeto desenvolvido para fins de portfólio profissional e demonstração de competências técnicas em FP&A, SQL e Análise de Dados.*
