# 1. Repositório

Este repositório contém uma análise detalhada da produtividade de equipamentos em uma indústria química, utilizando as bibliotecas Pandas, Pyplot e outras ferramentas do ecossistema Python. O estudo foi apresentado à liderança sênior de operações e às lideranças das áreas correlacionadas. Os dados foram resumidos e adaptados para preservar confidencialidade e facilitar a visualização de tendências e insights.


## 1.1 Contexto

O projeto foi desenvolvido com dados de produtividade de uma indústria química que produz mais de 120 produtos em aproximadamente 20 linhas de produção.

A empresa estabeleceu metas de produção por hora específicas para cada combinação de produto e equipamento. Diariamente, os dados de produção são reportados e comparados com as metas, permitindo avaliar o andamento do planejamento e identificar itens com baixa eficiência, com base na meta global (benchmark) de 85% de eficiência mínima. No final de cada mês, os resultados e os planos de ação são apresentados à liderança, incluindo a presidência.

Devido à grande quantidade de SKUs e equipamentos, torna-se complexo priorizar as ações para todos os produtos e equipamentos que não atingem a meta de eficiência. Para maximizar os resultados com maior eficiência e menor custo, é essencial priorizar os produtos que mais impactam a produtividade total, em vez de focar apenas naqueles com eficiência inferior a 85%. Este projeto buscou, com base em dados históricos (último 2 anos), determinar:
- Se as metas traçadas são realistas.
- Como priorizar poucos produtos que trouxessem maior impacto para a eficiência geral da empresa.

# 2. O Projeto

## 2.1 Jupyter Notebook / Google Colab

O projeto foi desenvolvido no Google Colab. Você pode acessá-lo clicando no link abaixo:

[Abrir](LINK)

## 2.2 Bibliotecas Utilizadas

Este projeto utilizou as seguintes bibliotecas:

- `Pandas`
- `matplotlib`
- `math`
- `python-pptx`
- `Pillow (PIL)`

## 2.3 Coleta dos Dados

Os dados foram coletados a partir de arquivos de Excel e do sistema ERP (SAP).

Arquivos coletados:
- **1. Lista de equipamentos.xlsx** - Planilha com informações dos equipamentos.
- **2. Lista SKU.xlsx** - Relatório do ERP detalhando os produtos.
- **3. PRODUCAO XX.xlsx** - Dados históricos de produção, coletados em tempo real por sensores.
- **4. Produtividade equipamentos.xlsx** - Planilha com metas de produtividade.

Uma análise inicial foi realizada para entender as variáveis disponíveis.

## 2.4 Limpeza dos Dados

A etapa de limpeza de dados incluiu os seguintes passos:

- **Materiais** com dados vazios foram removidos por se tratarem de sujeira do sistema ou subprodutos listados como subtotais nos relatórios do ERP.
- **Materiais** cujo código começava com "61" foram excluídos por serem produtos intermediários fora do escopo do projeto.
- Foi aplicado um filtro de **Quantidade** para valores entre -900 e 900, conforme acordado com as áreas produtivas. Valores fora deste intervalo foram considerados ajustes sistêmicos, sem relevância para a produção real.

## 2.5 Tratamento dos Dados e Análise Exploratória (EDA)

A etapa de tratamento e análise exploratória dos dados incluiu os seguintes passos:

- Agrupamento da produção por hora completa (ex.: 8:00, 9:00, 16:00) para comparação com as metas horárias.
- Mescla das tabelas para inclusão das metas de produção.
- Filtro para considerar apenas horas produtivas. Foram consideradas válidas apenas as horas com produção contínua (1 hora antes e 1 hora depois), desconsiderando intervalos de refeição e trocas de turno, para garantir que apenas períodos completos de produção fossem analisados.

## 2.6 Reporte

As tabelas e gráficos gerados foram exportados para Excel e PowerPoint, de acordo com as seguintes diretrizes:

- **PowerPoint**: Um resumo geral e detalhado foi gerado automaticamente em formato PPT, para ser enviado mensalmente ou sob demanda para líderes e equipes operacionais.
- **Excel**: Os dados foram exportados em formato adequado para que outros colaboradores possam aprofundar a análise ou adotar uma abordagem diferente.

#  3. Resultados
Para o relatório gerencial exportado em powerpoint, temos os seguintes gráficos apresentados
- Comparativo meta, mediana de produtividade e máxima capacidade histórica por tipo de embalagem
- Mapa produtividade (%) vs quantidade de horas por equipamento/hora para priorização do plano de ação
- Resumo por equipamento da distribuição histórica de produtividade vs meta e mediana (1 slide por equipamento)



# 3.1 Metas
Foi feito para cada tipo de embalagem, um gráfico da mediana, meta e máximo para comparativo, conforme gráfico abaixo. Pode-se constatar que dos 20 equipamentos, apenas 3 não tiveram um valor máximo de produtividade (L/h) maior ou igual a meta (por exemplo, o EQ-3 para 2L, conforme gráfico abaixo - máximo de 8300 vs meta de 10.000. Para esses equipamentos, foi solicitado a engenharia fazer uma análise mais apronfundada se necessitamos fazer alguma adequação ou reforma do equipamento para atingimento da meta ou se seria necessário reduzir a meta no planejamento.




![Produtividade por equipamento](./Images/Produtividade%202L%20por%20equipamento.PNG)

# 3.2 Mapa de produtividade
Foi feito uma visão sumarizada da produvidade vs quantidade de horas produzidas para as combinações equipamentos/SKU. Com isso, pode-se visualizar os principais equipamentos/SKUs que devem ser priorizados.
Dentro do retãngulo vermelho, temos 7 equipamentos/SKUs que representam 85% das horas produzidas, ou seja, são aqueles com maior impacto para produtividade da fábrica. 
A linha azul representa o threshold de 85% de produtividade. Acima, os equipamentos/SKUs (EQ-10 20L e EQ10 15L) estão acima da produtivididade mínima e estão ok. Abaixo (5 deles) são aqueles que é necessário priorizar para aumento de produtividade com destaque para o EQ7-12L representando quase 600h de produção e bem acima dos outros 4. Com isso, pode-se focar em poucos equipamentos/SKUs, reduzindo o custo de implementação de melhorias.

![Produtividade geral](./Images/Sumário%20Ajustado.PNG)

# 3.3 Resumo por equipamento
Para cada equipamento, foi feito um slide contendo um histograma da produtividade por SKU para verificação das produtividades mais frequentes, mediana do valor e meta. Abaixo um exemplo referente ao equipamento 18.

Pode-se notar que 
- Para SKU de 1L: Máximo e meta muito próximos, sem necessidade de revisão do valor da meta. Alta frequência de valores acima de 4.000, o que nos leva a concluir que temos um bom histórico com esse equipamento
- Para SKU de 6L: Máximo acima da meta., avaliar se seria factível reivsar as metas para cima, considerando o bom histórico. Dispersão muito alta para valores abaixo de 8.000, como plano de ação a área poderia investigar a alta variabilidade 

<img src="./Images/Produtividade%20EQ18.png" alt="Resumo por equipamento" width="2000"/>

