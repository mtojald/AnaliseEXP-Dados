# AnaliseEXP-Dados
## Como baixar o Banco de Dados
```
import kagglehub

# Download latest version
path = kagglehub.dataset_download("sibamsamanta07/movies-dataset-45k-films-with-budget-and-revenue")

print("Path to dataset files:", path)
``` 

## Etapa 1 - Pré Processamento

### Pré-processamento dos Dados

Antes da realização das análises estatísticas, foi necessário avaliar a
qualidade da base de dados. Nesta etapa, serão identificados valores
ausentes, registros duplicados, tipos de dados inadequados e outras
inconsistências que possam interferir nos resultados.

As decisões de tratamento serão tomadas considerando o significado de
cada variável, evitando a criação de informações artificiais.

### Tratamento de orçamento, receita e duração

Foi identificado que grande parte dos registros não possuía informações
válidas de orçamento e receita, sendo esses casos representados pelo valor
zero na base.

Como valores zerados poderiam distorcer as análises estatísticas, eles foram
tratados como dados ausentes (NaN).

Para as análises que dependem de orçamento, receita e duração, foi criada
uma amostra contendo somente registros com essas informações disponíveis.
A base geral possui 45.460 registros, enquanto a amostra resultante possui
5.369 filmes.

A base original tratada foi preservada para análises que não dependem dessas
variáveis.

# B. Análise Estatística

Após o pré-processamento, inicia-se a análise estatística dos filmes.

Para as análises financeiras, será utilizada a amostra `df_filmes_completos`,
composta apenas por filmes que possuem informações válidas de orçamento,
receita e duração.

Inicialmente, serão utilizadas medidas de centralização para compreender
como os valores de orçamento e receita estão distribuídos na amostra.

## Medidas de Centralização

Serão analisadas a média, mediana e moda.

- **Média:** representa o valor médio da variável.
- **Mediana:** representa o valor central dos dados quando ordenados.
- **Moda:** representa o valor que ocorre com maior frequência.

A comparação entre essas medidas também permite identificar possíveis
assimetrias e influência de valores extremos.

### Análise do orçamento

O orçamento médio dos filmes da amostra é de aproximadamente US$ 31,2 milhões,
enquanto a mediana é de US$ 17 milhões. A diferença entre essas duas medidas
indica que a distribuição dos orçamentos pode apresentar assimetria, com
filmes de orçamento muito elevado aumentando o valor da média.

A moda encontrada foi de US$ 20 milhões, indicando que este é o valor de
orçamento que aparece com maior frequência na amostra.

Esses resultados mostram que a média, isoladamente, pode não representar
adequadamente o orçamento típico dos filmes da amostra, sendo importante
considerar também a mediana e outras medidas de distribuição.

### Análise da receita

A receita média dos filmes da amostra é de aproximadamente US$ 90,5 milhões,
enquanto a mediana é de US$ 30 milhões.

A diferença significativa entre média e mediana indica que a distribuição
das receitas pode apresentar forte assimetria, possivelmente devido à
existência de filmes com receitas muito superiores às demais.

A moda encontrada foi de US$ 12 milhões, indicando que este é o valor de
receita que aparece com maior frequência na amostra.

Assim como observado nos orçamentos, a média isoladamente pode não representar
adequadamente um valor típico de receita dos filmes analisados.

https://docs.google.com/document/d/19mkWK-X600ZnGFmysuBwuirgvl4rbzHqy7tcu8NKGjU/edit?usp=sharing
https://docs.google.com/spreadsheets/d/17DaHDj6l8P4jeTncjDNv83UqBjw2L46kO19Fu1yo1Xo/edit?usp=sharing
