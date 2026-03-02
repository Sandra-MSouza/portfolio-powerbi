# Portfólio Power BI — Dashboards e KPIs

Transformo dados em decisões. Este portfólio reúne dashboards criados no Power BI (DAX/Power Query), com foco em problemas reais de negócio e comunicação clara para tomada de decisão.

- Ferramentas: Power BI (DAX/Power Query), Excel, SQL, Python (pandas)
- Temas: modelagem (estrela), KPIs, data cleaning, visualização, storytelling

## Projetos

### 1) Vendas  — Receita, Margem e Ticket 
Problema: acompanhar receita, margem e ticket por período, produto e canal, entendendo sazonalidade e top performers.  
KPIs: Receita, Margem, Ticket Médio, Crescimento vs. Ano Anterior, Top N por produto/canal.  
Imagens:

### 2) Financeiro — Receitas, Despesas e Saldo
Problema: evoluções de receita, despesa e saldo mensal para decisões de orçamento e custos.  
KPIs: Receita, Despesa, Saldo, Variação M/M e A/A, Real vs. Orçado.  
Imagens:
-

### 3) Gestão Estoque I — OTIF, SLA e Giro
Problema: melhorar nível de serviço e disponibilidade com monitoramento de prazos e rupturas.  
KPIs: OTIF, SLA cumprido, Lead time, Ruptura %, Giro de estoque, Cobertura (dias).  
Imagens:

### 4) Dados Funcionários I (RH) — Turnover, Absenteísmo e Remuneração
Problema: entender rotatividade, ausências e remuneração por área/cargo para decisões de pessoas.  
KPIs: Turnover %, Absenteísmo %, Tempo médio de casa, Remuneração média, Contratações/Saídas.  
Imagens:

### 5) Produção Veículos I — Volume por Categoria e Tendências
Problema: acompanhar produção por tipo/categoria ao longo do tempo e por região/planta.  
KPIs: Volume produzido, Capacidade utilizada, Tendência por categoria, Mix de produção.  
Imagens:

## Processo e Modelagem 
- ETL no Power Query: limpeza, tipos e padronização de categorias.
- Modelagem em esquema estrela: tabela fato + dimensões (Calendário, Produto/Cliente/Área, etc.).
- DAX para KPIs e comparativos (YoY, M/M, Top N, contribuições).

___________________________________________________________________________________________________________________________________________________________
## Medidas DAX 
```DAX
-- Ticket Médio
Ticket Médio = DIVIDE([Receita], SUM(F_Vendas[Quantidade]))

-- Crescimento vs Ano Anterior
Crescimento vs LY % =
VAR atual = [Receita]
VAR passado = CALCULATE([Receita], DATEADD('Calendario'[Data], -1, YEAR))
RETURN DIVIDE(atual - passado, passado)

--Tabela Calendadrio 

Calendario =
VAR DATAMINIMA = MIN( 'Tabela_Fato'[Data] ) 
VAR DATAMAXIMA = MAX( 'Tabela_Fato'[Data] ) 

RETURN
    ADDCOLUMNS (
        CALENDAR (DATAMINIMA, DATAMAXIMA),  
        "Ano", YEAR([Date]),  
        "Mês", MONTH([Date]),  
        "Dia", DAY([Date]),  
        "Nome do Mês", UPPER(FORMAT([Date], "mmm")),
        "Dia da semana", WEEKDAY([Date],2),
        "Nome do dia da semana", FORMAT([Date], "ddd"),
        "Trimestre", "Q" & FORMAT([Date], "Q"),
        "Ano-Mês", FORMAT([Date], "YYYY-MM"),
        "Semestre", "S" & CEILING(MONTH([Date]) / 6, 1)
    )
______________________________________________________________________________________________________________________________


## 📬 Contato

* 🔗 [LinkedIn](https://linkedin.com/in/sandramssouza)
* 💻 [GitHub](https://github.com/Sandra-MSouza)
* ✉️ [Email](san.mssouza@gmail.com)
---

**Obrigada por visitar!** Estou aberta a conexões, feedbacks e oportunidades na área de Análise de Dados.
**Thank you for visiting!** I’m open to networking, feedback, and opportunities in Data Analysis.
