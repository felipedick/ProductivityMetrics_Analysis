# 1. Repositório

Este repositório contém uma análise detalhada da produtividade de equipamentos em uma indústria química, utilizando as bibliotecas Pandas, Pyplot e outras ferramentas do ecossistema Python. O estudo foi apresentado à liderança sênior de operações e às lideranças das áreas correlacionadas. Os dados foram resumidos e adaptados para preservar confidencialidade e facilitar a visualização de tendências e insights.


## 1.1 Contexto

O projeto foi desenvolvido com dados de produtividade de uma indústria química que fabrica mais de 120 produtos em aproximadamente 20 linhas de produção. Existem cerca de 10 tipos de embalagens, embora nem todos os equipamentos processem todas elas, resultando em 48 combinações distintas de equipamento/SKU.

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
- **3. PRODUCAO ENVASE BALANCA.xlsx** - Dados históricos de produção, coletados em tempo real por sensores.
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
- Comparativo entre meta, mediana de produtividade e capacidade máxima histórica por tipo de embalagem.
- Mapa de produtividade (%) versus quantidade de horas por equipamento/SKU, usado para priorizar o plano de ação.
- Resumo por equipamento com a distribuição histórica de produtividade versus meta e mediana por SKU (1 slide por equipamento).



# 3.1 Metas
Para cada tipo de embalagem, foi criado um gráfico comparativo entre a mediana, a meta e o máximo histórico de produtividade. 
Durante o estudo, constatamos que, dos 48 equipamentos analisados, apenas 3 não atingiram um valor máximo de produtividade (L/h) igual ou superior à meta. Por exemplo, o equipamento EQ-3 para embalagens de 2L alcançou um máximo de 8.300 L/h, abaixo da meta de 10.000 L/h (conforme o gráfico abaixo). Nesses casos, a equipe de engenharia foi acionada para avaliar se são necessárias adequações ou reformas nos equipamentos, ou se a meta deve ser ajustada no planejamento.



![Produtividade por equipamento](./Images/Produtividade%202L%20por%20equipamento.PNG)

# 3.2 Mapa de produtividade
Foi gerado um gráfico de produtividade versus quantidade de horas produzidas por equipamento/SKU, destacando as principais combinações a serem priorizadas. No retângulo vermelho, identificamos 7 equipamentos/SKUs que representam 85% das horas produzidas, sendo os de maior impacto na produtividade da fábrica.

A linha azul marca o limite de 85% de produtividade. Equipamentos/SKUs acima dessa linha (como EQ-10 20L e EQ-10 15L) estão dentro do esperado. Já os 5 equipamentos/SKUs dentro do retângulo vermelho, mas abaixo da linha, requerem ações prioritárias para aumento de produtividade. Isso permite um foco mais eficiente e redução de custos nas melhorias. Dentre eles, destaca-se o EQ7-12L, com quase 600 horas de produção, que demanda atenção especial.


![Produtividade geral](./Images/Sumário%20Ajustado.PNG)

# 3.3 Resumo por equipamento
Para cada equipamento, foi criado um slide contendo um histograma da produtividade por SKU, destacando os valores mais frequentes, a mediana e a meta de produtividade. Abaixo, um exemplo do equipamento 17:

- SKU 3L: A máxima produtividade está muito próxima da meta, indicando que não é necessário revisar o valor da meta. Há uma alta frequência de valores acima de 4.000 L/h, demonstrando um bom desempenho histórico do equipamento.
- SKU 20L: A máxima produtividade está acima da meta, sugerindo que é possível revisar as metas para cima, dado o bom desempenho histórico. No entanto, há uma alta dispersão de valores abaixo de 8.000 L/h, o que indica a necessidade de investigar a variabilidade e tomar ações corretivas.

![Produtividade EQ17](./Images/Produtividade%20EQ17.png)

# 4.0 Conclusão
O estudo revelou a necessidade de revisar ao menos 3 das metas estabelecidas, o que demonstra, no geral, uma boa qualidade na definição das metas dos equipamentos, com **94% de acurácia**. Além disso, a análise permitiu concentrar os esforços em apenas 5 equipamentos/SKUs, **uma redução de cerca de 90% em relação às 48 combinações totais. Isso gera maior eficiência e contribui para a redução de custos da empresa.**

Como se trata de um processo semi-automático de geração de relatórios, que exige apenas o download do histórico de produção, ele pode ser facilmente executado mensalmente. Isso permite **acompanhar o status** das produtividades e comparar com os meses anteriores, facilitando a análise da **evolução das ações e da produtividade.**
