# O que é regressão?

A regressão funciona estabelecendo uma relação entre variáveis nos dados que representam características — conhecidas como recursos — da coisa que está sendo observada e a variável que estamos tentando prever — conhecida como rótulo . Lembre-se de nossa empresa que aluga bicicletas e deseja prever o número esperado de locações em um determinado dia. Nesse caso, os recursos incluem coisas como dia da semana, mês e assim por diante, enquanto o rótulo é o número de aluguéis de bicicletas.

Para treinar o modelo, começamos com uma amostra de dados contendo os recursos, bem como valores conhecidos para o rótulo - portanto, neste caso, precisamos de dados históricos que incluam datas, condições climáticas e o número de aluguéis de bicicletas.

Em seguida, dividiremos essa amostra de dados em dois subconjuntos:

Um conjunto de dados de treinamento ao qual aplicaremos um algoritmo que determina uma função que encapsula a relação entre os valores de recurso e os valores de rótulo conhecidos.
Um conjunto de dados de validação ou teste que podemos usar para avaliar o modelo usando-o para gerar previsões para o rótulo e compará-las com os valores de rótulo conhecidos reais.
O uso de dados históricos com valores de rótulo conhecidos para treinar um modelo torna a regressão um exemplo de aprendizado de máquina supervisionado .

# Um exemplo simples
Vamos dar um exemplo simples para ver como o processo de treinamento e avaliação funciona em princípio. Suponha que simplifiquemos o cenário para usarmos um único recurso – temperatura média diária – para prever a etiqueta de aluguel de bicicletas. </p> 

Continuaçao. </P>
Link: https://learn.microsoft.com/en-us/training/modules/train-evaluate-regression-models/2-what-is-regression

Começamos com alguns dados que incluem valores conhecidos para o recurso de temperatura média diária e o rótulo de aluguel de bicicletas.

# Regressão linear múltipla e R-quadrado

Nesta unidade, contrastaremos a regressão linear múltipla com a regressão linear simples . Também veremos uma métrica chamada R 2 , que é comumente usada para avaliar a qualidade de um modelo de regressão linear.

# Regressão linear múltipla
A regressão linear múltipla modela a relação entre vários recursos e uma única variável. Matematicamente, é o mesmo que a regressão linear simples e geralmente é ajustada usando a mesma função de custo, mas com mais recursos.

Em vez de modelar um único relacionamento, essa técnica modela simultaneamente vários relacionamentos, que trata como independentes um do outro. Por exemplo, se estivermos prevendo o quão doente um cachorro ficará com base em sua idade e body_fat_percentage, duas relações serão encontradas:

Como a idade aumenta ou diminui a doença
Como body_fat_percentage aumenta ou diminui a doença
Se estivermos trabalhando apenas com dois recursos, podemos visualizar nosso modelo como uma superfície plana 2D, assim como podemos modelar uma regressão linear simples como uma linha. Vamos explorar isso no próximo exercício.

# A regressão linear múltipla tem suposições
O fato de que o modelo espera que as características sejam independentes é chamado de suposição do modelo. Quando as suposições do modelo não são verdadeiras, o modelo pode fazer previsões enganosas.

Por exemplo, a idade provavelmente prediz como os cães ficam doentes, conforme os cães mais velhos ficam mais doentes, juntamente com se os cães foram ensinados a jogar frisbee: cães mais velhos provavelmente sabem jogar frisbee. Se incluíssemos idade e know_frisbee em nosso modelo como recursos, provavelmente nos diria que know_frisbee é um bom preditor de uma doença e subestimaríamos a importância da idade. Isso é um pouco absurdo, porque saber que o frisbee provavelmente não causa doenças. Por outro lado, dog_breed também pode ser um bom preditor de doença, mas não há razão para acreditar que idade prediz dog_breed, então seria seguro incluir ambos em um modelo.

# Qualidade do ajuste: R 2
Sabemos que as funções de custo podem ser usadas para avaliar o quão bem um modelo se ajusta aos dados nos quais é treinado. Os modelos de regressão linear têm uma medida relacionada especial chamada R 2 (“R-quadrado”). R 2 é um valor entre 0 e 1 que nos diz o quão bem um modelo de regressão linear ajusta os dados. Quando as pessoas falam sobre as correlações serem fortes, geralmente querem dizer que o valor de R 2 era grande.

R 2 usa a matemática além do que pretendemos abordar neste curso, mas podemos pensar nisso intuitivamente. Vamos considerar o exercício anterior em que examinamos a relação entre idade e core_temperature. Um R 2 de 1 significaria que anos poderiam ser usados para prever perfeitamente quem tinha temperatura alta e quem tinha temperatura baixa. Em contraste, um 0 significaria simplesmente que não havia relação entre anos e temperatura.

Exemplo: </p>
</p>
<img src="https://user-images.githubusercontent.com/91704169/232543355-add4c093-2891-45d4-b786-72da560ef21f.png" width="1000px" align="centter" alt="planos">

A realidade está em algum lugar no meio. Nosso modelo pode prever a temperatura até certo ponto (então é melhor que R 2 = 0), mas os pontos variaram um pouco dessa previsão (portanto, é menor que R 2 =1).

R 2 é apenas metade da história

Os valores de R 2 são amplamente aceitos, mas não são uma medida perfeita que possamos usar isoladamente. Eles sofrem quatro limitações:

Por causa de como o R 2 é calculado, quanto mais amostras tivermos, maior será o R 2 . Isso pode nos levar a pensar que um modelo é melhor que outro modelo (idêntico), simplesmente porque os valores de R 2 foram calculados usando diferentes quantidades de dados.
Os valores de R 2 não nos dizem quão bem um modelo funcionará com dados novos e inéditos. Os estatísticos superam isso calculando uma medida suplementar, chamada valor-p, que não abordaremos aqui. No aprendizado de máquina, geralmente testamos explicitamente nosso modelo em outro conjunto de dados.
Os valores de R 2 não nos dizem a direção do relacionamento. Por exemplo, um valor de R 2 de 0,8 não nos diz se a linha é inclinada para cima ou para baixo. Também não nos diz quão inclinada é a linha.
Também vale a pena ter em mente que não há critérios universais para o que torna um valor de R 2 “bom o suficiente”. Por exemplo, na maior parte da física, é improvável que correlações que não sejam muito próximas de 1 sejam consideradas úteis, mas, ao modelar sistemas complexos, valores de R 2 tão baixos quanto 0,3 podem ser considerados excelentes.
