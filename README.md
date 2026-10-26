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
O Quarto produz `index.html`, com resultados e graficos incorporados. So publique o HTML apos executar e conferir os resultados com a base original.
Entregaveis
Saida	Local
Indicadores principais	`outputs/tables/kpis.csv`
Vendas por mes	`outputs/tables/mensal.csv`
GMV por estado do cliente	`outputs/tables/estados.csv`
Pontualidade x avaliacao	`outputs/tables/satisfacao_entrega.csv`
Recorrencia observada	`outputs/tables/recompra.csv`
Qualidade do recorte	`outputs/tables/qualidade.csv`
Graficos	`outputs/figures/*.png`
Relatorio navegavel	`index.html`
Metodologia e ressalvas
Unidade de analise: um pedido entregue com itens; a tabela de itens e agregada antes da integracao para nao multiplicar o GMV.
GMV: soma do preco dos produtos (`price`) sem frete; nao representa receita liquida da plataforma nem comissao.
Ticket medio: GMV total dos produtos dividido pelo total de pedidos analisados.
Pontualidade: dia real de entrega ate o dia estimado, inclusive. Pedidos sem ambas as datas ficam fora do calculo da pontualidade.
Avaliacao: quando ha mais de um registro de avaliacao para o mesmo pedido, usa-se a avaliacao mais recente.
Recorrencia: clientes com pelo menos dois pedidos entregues no recorte / clientes unicos com pedido entregue. Nao equivale a retencao de longo prazo.
Escopo: dataset historico de 2016–2018; primeiros/ultimos meses podem ser incompletos. Comparacoes de atrasos e notas mostram associacao, nao causalidade.
Validacao antes de divulgar resultados
Confira se `total_pedidos_entregues` e inferior ou igual ao numero de pedidos entregues da base original.
Confirme que o numero de linhas nao cresce apos os joins de clientes/avaliacoes.
Verifique `qualidade.csv`, em especial datas ausentes e pedidos sem itens.
Leia os graficos e escreva 2–3 descobertas somente com os numeros efetivamente calculados.
Diferencie explicitamente dados historicos da situacao atual.
Como publicar no GitHub
Crie um repositorio publico chamado `olist-r-analytics`.
Envie os scripts, `README.md`, `relatorio.qmd`, graficos, CSVs agregados e `index.html`.
Mantenha os arquivos CSV originais em `data/raw/` fora do repositorio (configurado em `.gitignore`) e vincule a fonte Kaggle.
Em Settings > Pages > Build and deployment, selecione Deploy from a branch, `main` e `/(root)`.
Depois de publicada, a pagina geralmente fica em `https://SEU_USUARIO.github.io/olist-r-analytics/` (confirme o link fornecido pelo GitHub).
Insira no portfolio o link para o repositorio, o relatorio e uma miniatura de um dos graficos.
Melhorias futuras
Analise de coortes/RFM com definicoes explicitas e censura temporal.
Series de atraso por estado e mes.
Dashboard interativo em Shiny.
Testes estatisticos com grupos adequados e analise de variaveis de confusao.
Captura automatizada dos dados com versoes controladas quando os termos de acesso permitirem.
Creditos: Dataset Olist no Kaggle, utilizado para fins educacionais; projeto, codigo e analises a cargo do autor.
