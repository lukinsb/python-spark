# Python - Spark


Teste com dataset HTTP Requests From NASA KSC 


# Questões 

1- Qual o objetivo do comando  **cache** em Spark?

O comando cache instrui ao Spark da necessidade de carregar um arquivo, stream de dados ou outro tipo de informação, em memória. Após solicitar um arquivo do armazenamento ou qualquer outro tipo de processo por meio do spark, para que estes dados sejam armazenados em memória para que sejam utilizados posteriormente é necessário que se utilize o comando cache por meio da sintaxe: *.cache.

2- O mesmo código implementado em Spark é normalmente mais rápido que a implementação equivalente em MapReduce. Por quê?

O principal motivo pelo qual um código implementado em Spark é, normalmente, 100x mais rápido que a sua implementação em Hadoop com MapReduce quando em memória, ou 10x mais rápido em disco, se deve ao fato de todo o processamento em Spark ser realizado diretamente na memória principal do node Spark em que o código está rodando, não necessitando de todo o stack de trocas de informação (I/O operations, operações de troca de dados) entre o Hadoop e o hardware. Portanto, a utilização do Spark reduz muito operações em disco, que se tornam desnecessárias pelo método com que este roda os códigos.

3 - Qual a função do  **Spark Context**?

O Spark context é "portão de entrada" de todas as funcionalidades do Apache Spark. Gerar o Spark Context é uma das principais tarefas esperadas de uma aplicação Spark. O Spark Context possibilita o acesso ao Cluster Spark e é ccriado após o comando SparkConf.

4 - Explique com suas palavras o que é  **Resilient Distributed Datasets**  (RDD).

RDD's são a estrutura fundamental de dados do Spark, a forma como o Spark representa e armazena seus dados de forma distribuida em diversas máquinas (ou nodes), englobando, também, suas API's tornando possível acessar esses dados. Devido a descentralização dos dados é possível garantir alta taxa de persistência e disponibilidade dos dados, visto que são armazenados de forma redundante e como um "dataset" particionado por diversos servidores.

5 -  **GroupByKey**  é menos eficiente que  **reduceByKey**  em grandes datasets. Por quê?

Em maiores datasets o comando "reduceByKey" tem melhor desempenho, visto que com ele o Spark consegue combinar os resultados diferentes partições em uma mesma "chave comum", equanto o "groupByKey" somente agrupa o dataset resultando em uma combinação dos dados antes da sua separação entre os clusteres pelo RDD. O "reduceByKey" pode-ser dizer que agrupa e agrega os dados, por um indice, sem movê-los realmente, mantendo-os distribuidos o comando realiza menor movimentação dos dados economizando memória e operações.

6 - O que o código Scala abaixo faz?

O código descrito acima realiza as seguintes funções em descrição linha a linha:

1.  Cria a variável textFile e armazena o conteudo de um arquivo texto carregado de um sistema de dados distribuidos HDFS para a mesma;
    
2.  Cria a variável counts e faz seu "assign" para itens "mapeados" (extraidos a partir de regras) do texto carregado na variável textFile, os valores mapeados para counts serão as palavras contidas no texto, porém separando-as palavra a palavra em cada linha por meio de seus espaços.
    
3.  Dentro do map anterior cada linha recebe outro comando map, com cada palavra sendo colocada em um arranjo (tupla) numérico, com um índice para cada palavra
    
4.  Ainda dentro do primeiro map é feita uma redução (reduce) com os itens sendo agragados por underscores.
    
5.  A variável counts é armazenada como um arquivo de texto após a realização dos comandos Map e Reduce

## Data handling
Todo o código desenvolvido se encontra no arquivo .ipynbna raiz do repositório, junto com as questões respondidas.

1. Numero de hosts unicos: 137979 

2. Numero total de erros 404: 20901 

3. As 5 URLs que mais causaram erros 404: 

| Url                                            |Ocorrências|
| ---------------------------------------------- | --------- |
| /pub/winvn/readme.txt                          | 2004      |
| /pub/winvn/release.txt                         | 1732      |
| /shuttle/missions/STS-69/mission-STS-69.html   | 683       |
| /shuttle/missions/sts-68/ksc-upclose.gif       | 428       |
| /history/apollo/a-001/a-001-patch-small.gif    | 384       |
 

4. Quantidade de erros 404 por dia: 

|    Data     | Ocorrências |
| ----------- | ----------- |
| 06/Jul/1995 |   640       |
| 19/Jul/1995 |   639       |
| 30/Aug/1995 |   571       |
| 07/Jul/1995 |   570       |
| 07/Aug/1995 |   537       |
| 13/Jul/1995 |   532       |
| 31/Aug/1995 |   526       |
| 05/Jul/1995 |   497       |
| 03/Jul/1995 |   474       |
| 12/Jul/1995 |   471       |
| 11/Jul/1995 |   471       |
| 18/Jul/1995 |   465       |
| 25/Jul/1995 |   461       |
| 20/Jul/1995 |   428       |
| 24/Aug/1995 |   420       |
| 29/Aug/1995 |   420       |
| 25/Aug/1995 |   415       |
| 14/Jul/1995 |   413       |
| 28/Aug/1995 |   410       |
| 17/Jul/1995 |   406       |
| 10/Jul/1995 |   398       |
| 08/Aug/1995 |   391       |
| 06/Aug/1995 |   373       |
| 27/Aug/1995 |   370       |
| 26/Aug/1995 |   366       |
| 04/Jul/1995 |   359       |
| 09/Jul/1995 |   348       |
| 04/Aug/1995 |   346       |
| 23/Aug/1995 |   345       |
| 27/Jul/1995 |   336       |
| 26/Jul/1995 |   336       |
| 21/Jul/1995 |   334       |
| 24/Jul/1995 |   328       |
| 15/Aug/1995 |   327       |
| 01/Jul/1995 |   316       |
| 10/Aug/1995 |   315       |
| 20/Aug/1995 |   312       |
| 21/Aug/1995 |   305       |
| 03/Aug/1995 |   304       |
| 08/Jul/1995 |   302       |
| 02/Jul/1995 |   291       |
| 22/Aug/1995 |   288       |
| 14/Aug/1995 |   287       |
| 09/Aug/1995 |   279       |
| 17/Aug/1995 |   271       |
| 11/Aug/1995 |   263       |
| 16/Aug/1995 |   259       |
| 16/Jul/1995 |   257       |
| 18/Aug/1995 |   256       |
| 15/Jul/1995 |   254       |
| 01/Aug/1995 |   243       |
| 05/Aug/1995 |   236       |
| 23/Jul/1995 |   233       |
| 13/Aug/1995 |   216       |
| 19/Aug/1995 |   209       |
| 12/Aug/1995 |   196       |
| 22/Jul/1995 |   192       |
| 28/Jul/1995 |    94       |
        

5. Total de bytes retornados: 61.0243 GB
## Instalação e Requisitos

* Numpy
* Pandas
* Python 3.7
* Ambiente Anaconda Jupyter Notebook

Para rodar basta apenas clonar o repositório e executar o arquivo no Jupyter Notebook direto da raiz do projeto.

### Licença
##### MIT


