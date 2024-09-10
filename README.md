# 1. Repositório

Este repositório contém uma análise abrangente da produtividade de equipamentos em uma indústria do mundo real, utilizando as bibliotecas Pandas, Pyplot e outras do Python.

## 1.1 Contexto

O projeto foi desenvolvido com dados de produtividade de uma indústria química que produz mais de 120 produtos em aproximadamente 20 linhas de produção.

A empresa estabeleceu metas de produção horária específicas para cada combinação de produto e equipamento. Diariamente, os dados de produção são reportados e comparados com as metas, permitindo avaliar o andamento do planejamento e identificar itens com baixa eficiência, com base na meta global de 85% de eficiência mínima. No final de cada mês, os resultados e os planos de ação são apresentados à liderança, incluindo a presidência.

Devido à grande quantidade de SKUs e equipamentos, torna-se complexo priorizar as ações para todos os produtos e equipamentos que não atingem a meta de eficiência. Para maximizar os resultados com maior eficiência e menor custo, é essencial priorizar os produtos que mais impactam a produtividade total, em vez de focar apenas naqueles com eficiência inferior a 85%. Este projeto buscou, com base em dados históricos, determinar:
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
- Resumo por equipamento da distribuição histórica de produtividade vs meta e mediana

# 3.1 Metas

