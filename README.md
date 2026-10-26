Brazilian E-Commerce — Sales & Customer Insights | R
Autor: Thiago Andrade  
Tecnologias: R, dplyr, readr, lubridate, ggplot2, Quarto, Git e GitHub  
Tema: Business Intelligence, analytics e experiencia do cliente  
Fonte: Brazilian E-Commerce Public Dataset by Olist
> Projeto de portfólio: análise reprodutível de vendas, prazos de entrega e avaliação de consumidores brasileiros usando uma amostra histórica de pedidos de 2016–2018.
English summary: End-to-end R analytics project exploring product GMV, order value, geographic trends, delivery timeliness, customer reviews, and observed repeat purchases in a historical Brazilian e-commerce dataset.
Perguntas de negócio
Como evoluiu o valor dos produtos vendidos (GMV) por mês?
Quais estados dos clientes concentram mais vendas?
Como as notas dos clientes variam entre entregas no prazo e atrasadas?
Qual parcela dos clientes observados tem dois ou mais pedidos entregues?
Estrutura
```text
olist-r-analytics/
├── Olist-R-Analytics.Rproj      # Projeto do RStudio
├── README.md                    # Apresentacao e metodologia
├── TUTORIAL.md                  # Passo a passo detalhado
├── relatorio.qmd                # Fonte do relatorio Quarto
├── scripts/
│   └── analise_olist.R         # Importacao, limpeza, joins, KPIs e graficos
├── data/raw/                   # Coloque os CSV originais aqui
└── outputs/
    ├── figures/                # Tres figuras PNG geradas
    └── tables/                 # CSVs de indicadores gerados
```
Como executar
1. Instale o R, o RStudio e, se necessario, o Quarto.
2. Descompacte este projeto e abra o arquivo `Olist-R-Analytics.Rproj`.
3. No Console do RStudio, instale os pacotes (apenas na primeira execucao):
```r
install.packages(c("dplyr", "readr", "lubridate", "ggplot2", "scales", "forcats", "knitr"))
```
4. Na pagina da base Olist no Kaggle, baixe e extraia o arquivo ZIP. Copie estes quatro CSVs para `data/raw/`:
`olist_orders_dataset.csv`
`olist_order_items_dataset.csv`
`olist_customers_dataset.csv`
`olist_order_reviews_dataset.csv`
5. No Console do RStudio, execute a partir da raiz do projeto:
```r
source("scripts/analise_olist.R")
```
6. Abra `relatorio.qmd` e clique em Render no RStudio; alternativamente, no Terminal do projeto:
```bash
quarto render relatorio.qmd
```
Series de atraso por estado e mes.
Dashboard interativo em Shiny.
Testes estatisticos com grupos adequados e analise de variaveis de confusao.
Captura automatizada dos dados com versoes controladas quando os termos de acesso permitirem.
Creditos: Dataset Olist no Kaggle, utilizado para fins educacionais; projeto, codigo e analises a cargo do autor.
