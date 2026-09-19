# AnaliseEXP-Dados
## Como baixar o Banco de Dados
```
import kagglehub

# Download latest version
path = kagglehub.dataset_download("sibamsamanta07/movies-dataset-45k-films-with-budget-and-revenue")

print("Path to dataset files:", path)
``` 

# Etapa 1 - Pré Processamento

## Pré-processamento dos Dados

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

# Etapa 2 - Análise Estatística

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

### Quartis do orçamento

A análise dos quartis mostra que 25% dos filmes da amostra possuem orçamento
de até US$ 5,2 milhões, enquanto 50% possuem orçamento de até US$ 17 milhões.

O terceiro quartil indica que 75% dos filmes possuem orçamento de até
US$ 40 milhões. Consequentemente, os 25% restantes apresentam orçamentos
superiores a esse valor.

O segundo quartil corresponde à mediana calculada anteriormente,
confirmando o valor de US$ 17 milhões.

### Quartis da receita

A análise dos quartis mostra que 25% dos filmes da amostra possuem receita
de até aproximadamente US$ 7,07 milhões.

A mediana indica que 50% dos filmes possuem receita de até US$ 30 milhões,
enquanto o terceiro quartil mostra que 75% apresentam receita de até
US$ 100 milhões.

Dessa forma, os 25% restantes apresentam receitas superiores a
US$ 100 milhões.

A diferença entre os quartis, juntamente com a média de aproximadamente
US$ 90,5 milhões observada anteriormente, indica uma grande variação
nas receitas dos filmes analisados.

### Amplitude do orçamento

O menor orçamento registrado na amostra foi de US$ 1, enquanto o maior foi
de US$ 380 milhões, resultando em uma amplitude de aproximadamente
US$ 380 milhões.

Durante a análise foram identificados diversos registros com orçamentos
extremamente baixos. Como não é possível determinar apenas pela base se
esses valores representam erros de registro ou casos reais, optou-se por
mantê-los na análise.

Esse resultado também demonstra uma limitação da amplitude como medida de
dispersão, pois ela considera apenas os valores mínimo e máximo e pode ser
fortemente influenciada por valores extremos. Sensível aos outliers

### Amplitude da receita

A menor receita registrada na amostra foi de US$ 1, enquanto a maior foi
de aproximadamente US$ 2,79 bilhões. Dessa forma, a amplitude das receitas
foi de aproximadamente US$ 2,79 bilhões.

A elevada amplitude demonstra a grande diferença existente entre os valores
extremos de receita da amostra. Entretanto, como essa medida considera
somente os valores mínimo e máximo, ela é bastante sensível à presença
de valores extremos.

### Desvio padrão do orçamento

O desvio padrão dos orçamentos foi de aproximadamente US$ 40,19 milhões,
valor superior ao orçamento médio de aproximadamente US$ 31,16 milhões.

Esse resultado indica uma elevada dispersão dos orçamentos na amostra,
ou seja, os valores apresentam grandes diferenças entre si.

Esse comportamento é consistente com a grande distância observada entre
os valores mínimo e máximo e com a diferença entre média e mediana.

### Variância do orçamento

A variância do orçamento foi de aproximadamente 1,61 × 10¹⁵.

O elevado valor indica uma grande dispersão dos orçamentos em relação à
média. Como a variância utiliza os desvios elevados ao quadrado, sua
interpretação direta é menos intuitiva.

Por esse motivo, o desvio padrão é uma medida mais adequada para interpretar
a dispersão neste contexto, pois é expresso na mesma unidade dos dados
originais.

### Dispersão da receita

A variância da receita foi de aproximadamente 2,76 × 10¹⁶, enquanto o
desvio padrão foi de aproximadamente US$ 166,28 milhões.

O desvio padrão é superior à própria receita média, que foi de
aproximadamente US$ 90,51 milhões. Isso indica uma elevada dispersão
dos valores de receita na amostra.

O resultado é consistente com as análises anteriores, nas quais foram
observadas grandes diferenças entre média e mediana e entre os valores
mínimo e máximo.

### Correlação entre orçamento e receita

Foi calculada a correlação de Pearson entre orçamento e receita, obtendo-se
um coeficiente de aproximadamente 0,730.

O resultado indica uma associação linear positiva considerável entre as
duas variáveis. Dessa forma, na amostra analisada, filmes com maiores
orçamentos tendem também a apresentar maiores receitas.

Entretanto, a correlação não implica causalidade. Portanto, o resultado
não permite concluir que o aumento do orçamento seja diretamente responsável
pelo aumento da receita, uma vez que outros fatores podem influenciar o
desempenho financeiro dos filmes.

### Normalização dos dados

As variáveis orçamento, receita e duração possuem unidades e escalas
diferentes, o que dificulta sua comparação direta.

Por esse motivo, foi aplicada a normalização por Z-score. Esse método
transforma os valores considerando sua distância em relação à média,
expressa em número de desvios padrão.

Após a transformação, as três variáveis apresentaram média próxima de
zero e desvio padrão igual a 1, confirmando que a normalização foi
realizada corretamente.

A transformação foi aplicada em uma cópia dos dados, preservando os
valores originais para as demais análises.

### Relação entre orçamento e receita

O gráfico de dispersão apresenta uma tendência positiva entre orçamento
e receita. De maneira geral, filmes com maiores orçamentos tendem a
apresentar receitas maiores.

Essa tendência é consistente com a correlação de Pearson calculada
anteriormente, cujo coeficiente foi de aproximadamente 0,730.

Apesar da relação positiva, observa-se uma dispersão considerável dos
pontos. Filmes com níveis semelhantes de orçamento podem apresentar
receitas bastante diferentes, indicando que o orçamento não é o único
fator associado ao desempenho financeiro.

Também são observados alguns valores extremos de receita, que contribuem
para a elevada dispersão identificada nas análises anteriores.

### Distribuição dos orçamentos

O histograma mostra que a distribuição dos orçamentos apresenta assimetria
à direita. A maior parte dos filmes está concentrada nas faixas de menor
orçamento, enquanto uma quantidade menor de filmes apresenta valores
consideravelmente mais elevados.

Essa distribuição ajuda a explicar a diferença observada anteriormente
entre a média e a mediana. Os filmes com orçamentos muito elevados aumentam
a média, fazendo com que ela seja superior à mediana.

O gráfico também é consistente com o elevado desvio padrão encontrado,
demonstrando a grande dispersão dos orçamentos da amostra.

### Distribuição das receitas

O histograma das receitas apresenta uma forte assimetria à direita.
A maior parte dos filmes está concentrada nas faixas de menor receita,
enquanto uma pequena quantidade apresenta receitas muito elevadas.

Esse comportamento explica a grande diferença observada entre a receita
média, de aproximadamente US$ 90,51 milhões, e a mediana, de
US$ 30 milhões.

Os filmes com receitas extremamente elevadas aumentam significativamente
a média e também contribuem para o elevado desvio padrão observado
anteriormente.

### Pergunta 1 — Filmes com maiores durações são menos vistos?

Como a base de dados não possui uma variável que represente diretamente
a quantidade de espectadores, foi utilizada a variável `popularity` como
um indicador aproximado do interesse do público.

Foi calculada a correlação de Pearson entre duração e popularidade,
obtendo-se um coeficiente de aproximadamente 0,110.

O valor indica uma correlação positiva muito fraca entre as variáveis.
Portanto, nesta amostra, não foi identificada uma relação linear relevante
que indique que filmes mais longos apresentam menor popularidade.

Dessa forma, os resultados obtidos não sustentam a hipótese inicial de que
filmes de menor duração são necessariamente mais populares.

Também não é possível atribuir esse comportamento a fatores geracionais,
como o consumo de conteúdos curtos em redes sociais, pois essa relação não
é medida diretamente pelo conjunto de dados analisado.
Como análise complementar, também foi calculada a correlação entre duração
e quantidade de votos (`vote_count`), obtendo-se aproximadamente 0,107.

Assim como ocorreu com a popularidade, o resultado representa uma correlação
positiva muito fraca. Os dois indicadores analisados, portanto, não apresentam
evidências de que filmes mais longos sejam necessariamente menos populares
ou recebam menor engajamento do público.

### Pergunta 2 — Existe relação entre orçamento e popularidade?

Foi calculada a correlação de Pearson entre orçamento e popularidade,
obtendo-se um coeficiente de aproximadamente 0,369.

O resultado indica uma associação positiva entre as variáveis, porém de
intensidade limitada. Dessa forma, filmes com maiores orçamentos apresentam
certa tendência a possuir maior popularidade, mas o orçamento isoladamente
não apresenta uma relação linear forte com essa variável.

Como comparação, a correlação entre orçamento e receita calculada
anteriormente foi de aproximadamente 0,730, indicando uma associação
consideravelmente maior.

Portanto, na amostra analisada, o orçamento apresenta uma relação mais
forte com a receita do que com a popularidade.

É importante destacar que as correlações representam associações e não
permitem concluir que um orçamento maior cause diretamente maior
popularidade ou receita.
https://docs.google.com/document/d/19mkWK-X600ZnGFmysuBwuirgvl4rbzHqy7tcu8NKGjU/edit?usp=sharing
https://docs.google.com/spreadsheets/d/17DaHDj6l8P4jeTncjDNv83UqBjw2L46kO19Fu1yo1Xo/edit?usp=sharing
