Qual o objetivo do comando cache em Spark?
Armazenar em memória os dados mapeados de um RDD.

O mesmo código processado em Spark é normalmente mais rápido que a implementação equivalente em MapReduce. Por quê?
Porque o Spark trabalha todo o processamento dos dados em memória, já o MapReduce requer a gravação dos dados em disco após o processamento.

Qual é a função do SparkContext?
Criar uma instância de conexão para um cluster Spark, e assim pode ser usado para criar RDDs, acumuladores e variáveis de transmissão para o cluster.

Explique com suas palavras o que é Resilient Distributed Datasets (RDD):
É uma estrutura de coleção de dados que são distribuídos através de múltiplos nós de um cluster. É resiliente devido a ser tolerante a falhas, tendo a capacidade de recuperar partições com falhas em um ou mais nós do cluster. É o core do Spark.

GroupByKey é menos eficiente que reduceByKey em grandes dataset. Por quê?
Porque ele não realiza a mesclagem dos valores chave da partição antes de espalhar os dados assim como faz o reduceByKey, e por consequência muitos dados podem acabar trafegando nas partições de um dataset.

Explique o que o código Scala abaixo faz:


val textFile = sc . textFile ( "hdfs://..." )
val counts = textFile . flatMap ( line => line . split ( " " ))
. map ( word => ( word , 1 ))
. reduceByKey ( _ + _ )
counts . saveAsTextFile ( "hdfs://..." )

Executa a leitura de um arquivo contendo strings, separando as strings por linha e atribuindo a ela um valor int para ser utilizado como contador. Depois executa a função reduceByKey para agrupar os dados por string que é o valor chave,  incrementando o valor de contador para indicar quantas ocorrências da mesma string foram mapeadas dentro do arquivo. E por fim salva o arquivo dataset com o resultado do processamento.







