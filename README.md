# Análise de Produtividade de Equipamentos na Indústria Química

Este repositório contém uma análise detalhada da produtividade de equipamentos em uma indústria química, utilizando as bibliotecas Pandas, Pyplot e outras ferramentas do ecossistema Python. A análise ajudou a reduzir em **90%** os itens a serem analisados para criar planos de ação e confirmou a acurácia de **94%** das metas traçadas.

## Contexto

A empresa fabrica mais de 120 produtos em 20 linhas de produção e utiliza 10 tipos de embalagens, resultando em 48 combinações de equipamentos e SKUs. A meta de eficiência é de, no mínimo, **85%**, sendo essencial priorizar os itens que mais impactam a produtividade.

O objetivo deste estudo foi:
- Avaliar se as metas estabelecidas são realistas.
- Priorizar produtos que mais afetam a eficiência geral.

## O Projeto

### Jupyter Notebook / Google Colab
O projeto foi desenvolvido no Google Colab. Você pode acessá-lo através do link:
[Ver Projeto no Colab](LINK)

### Bibliotecas Utilizadas
- `Pandas`
- `Matplotlib`
- `Math`
- `python-pptx`
- `Pillow`

### Coleta e Limpeza de Dados

**Fonte de dados:**
- Planilhas Excel e ERP (SAP)

**Arquivos coletados:**
- `Lista de equipamentos.xlsx`
- `Lista SKU.xlsx`
- `Produção Envasada.xlsx`
- `Produtividade Equipamentos.xlsx`

**Processos de Limpeza:**
- Remoção de dados vazios e irrelevantes (subprodutos, ajustes sistêmicos).
- Exclusão de SKUs intermediários e fora do escopo.
- Aplicação de filtros para valores de produção realistas.

## Análise de Dados

A análise exploratória incluiu:
- Agrupamento de produção por hora completa.
- Comparação com metas horárias.
- Filtros para horas produtivas (sem intervalos de refeição ou trocas de turno).

## Resultados

### 1. Metas de Produtividade
Foi constatado que apenas 3 dos 48 equipamentos não atingiram a meta de produtividade máxima. Para esses, foram iniciadas avaliações de engenharia ou ajustes nas metas.

**Quick win**: Identificamos oportunidades para priorizar os recursos com melhor produtividade para cada SKU, obtendo ganhos imediatos de eficiência sem custos adicionais. Por exemplo, o equipamento EQ-8 apresentou uma mediana de produtividade superior para embalagens de 2L, enquanto o EQ-1 e o EQ-3 tiveram desempenho inferior e devem ser evitados para este SKU.

**Ação pendente:** Avaliar os fatores que contribuem para a maior eficiência operacional do EQ-8 em relação aos outros. Isso pode incluir análise de dados do equipamento, como modelo, marca, ano, ou fatores operacionais, como os parâmetros de operação e o operador responsável.

![Produtividade por equipamento](./Images/Produtividade%202L%20por%20equipamento.PNG)

### 2. Mapa de Produtividade

Análise de Produtividade: Identificamos que 7 equipamentos/SKUs (representando 15% do total) são responsáveis por 85% das horas produtivas da fábrica. Entre eles, 5 apresentaram produtividade abaixo da meta mínima estabelecida, e foram priorizados para ações corretivas, visando aumentar sua eficiência e impactar significativamente a produtividade geral.



![Produtividade geral](./Images/Sumário%20Ajustado.PNG)

### 3. Resumo por Equipamento
Um slide para cada equipamento foi criado, destacando a produtividade por SKU, a mediana e as metas, permitindo análises detalhadas de desempenho e variação.

![Produtividade EQ17](./Images/Produtividade%20EQ17.png)

## Conclusão

O estudo confirmou que **94% das metas estabelecidas** são realistas. A priorização de apenas 5 SKUs/equipamentos (10% do total) resultou em uma **redução de 90% na quantidade de itens analisados**, otimizando o processo de tomada de decisão e gerando eficiência na produção.

Além disso, o processo é semi-automático, permitindo **acompanhar o status** periodicamente das produtividades e comparar com os meses anteriores, facilitando a análise da **evolução das ações e da produtividade.**

---

## Contato

Caso tenha dúvidas ou sugestões, sinta-se à vontade para abrir uma issue ou contribuir com o projeto.


