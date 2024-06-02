# Desafio Dio - **Criando seu Ecossistema de Big Data na Nuvem** 



### **Projeto: Criando seu Ecossistema de Big Data na Nuvem**

### **Programas e Códigos:**

#### **1. Instalação do Hadoop no Ubuntu:**

bash

```bash
sudo apt-get update
sudo apt-get install openjdk-8-jdk
wget https://dlcdn.apache.org/hadoop/common/hadoop-3.3.1/hadoop-3.3.1.tar.gz
tar -xzvf hadoop-3.3.1.tar.gz
sudo mv hadoop-3.3.1 /opt/hadoop
sudo chown -R hdfs:hdfs /opt/hadoop
sudo nano /etc/profile
```



#### **Adicione as seguintes linhas ao final do arquivo:**

bash

```bash
export HADOOP_HOME=/opt/hadoop
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_YARN_HOME=$HADOOP_HOME
export PATH=$PATH:$HADOOP_HOME/bin
export PATH=$PATH:$HADOOP_HOME/sbin
```



#### **Salve o arquivo e execute:**

bash

```bash
source /etc/profile
```



#### **2. Configuração do Hadoop:**

#### **core-site.xml:**

xml

```xml
<configuration>
  <property>
    <name>fs.defaultFS</name>
    <value>hdfs://localhost:9000</value>
  </property>
</configuration>
```



#### **hdfs-site.xml:**

xml

```xml
<configuration>
  <property>
    <name>dfs.replication</name>
    <value>1</value>
  </property>
</configuration>
```



#### **yarn-site.xml:**

xml

```xml
<configuration>
  <property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
  </property>
</configuration>
```



#### **3. Formatação do HDFS:**

bash

```bash
hdfs namenode -format
```



#### **4. Inicialização do Hadoop:**

bash

```bash
start-dfs.sh
start-yarn.sh
```



#### **5. Verificação do status do Hadoop:**

bash

```bash
jps
```



#### **6. Instalação do Apache Spark:**

bash

```bash
wget https://dlcdn.apache.org/spark/spark-3.3.1/spark-3.3.1-bin-hadoop3.2.tgz
tar -xzvf spark-3.3.1-bin-hadoop3.2.tgz
sudo mv spark-3.3.1-bin-hadoop3.2 /opt/spark
sudo chown -R spark:spark /opt/spark
sudo nano /etc/profile
```



#### **Adicione as seguintes linhas ao final do arquivo:**

bash

```bash
export SPARK_HOME=/opt/spark
export PATH=$PATH:$SPARK_HOME/bin
export PATH=$PATH:$SPARK_HOME/sbin
```



#### **Salve o arquivo e execute:**

bash

```bash
source /etc/profile
```



#### **7. Instalação do Apache Hive:**

bash

```bash
wget https://dlcdn.apache.org/hive/hive-3.1.2/apache-hive-3.1.2-bin.tar.gz
tar -xzvf apache-hive-3.1.2-bin.tar.gz
sudo mv apache-hive-3.1.2-bin /opt/hive
sudo chown -R hive:hive /opt/hive
sudo nano /etc/profile
```



#### **Adicione as seguintes linhas ao final do arquivo:**

bash

```bash
export HIVE_HOME=/opt/hive
export PATH=$PATH:$HIVE_HOME/bin
```



#### **Salve o arquivo e execute:**

bash

```bash
source /etc/profile
```



#### **8. Instalação do Apache Pig:**

bash

```bash
wget https://dlcdn.apache.org/pig/pig-20.1.0/pig-20.1.0.tar.gz
tar -xzvf pig-20.1.0.tar.gz
sudo mv pig-20.1.0 /opt/pig
sudo chown -R pig:pig /opt/pig
sudo nano /etc/profile
```



#### **Adicione as seguintes linhas ao final do arquivo:**

bash

```bash
export PIG_HOME=/opt/pig
export PATH=$PATH:$PIG_HOME/bin
```



#### **Salve o arquivo e execute:**

bash

```bash
source /etc/profile
```



#### **9. Instalação do Apache Oozie:**

bash

```bash
wget https://dlcdn.apache.org/oozie/oozie-5.1.0/apache-oozie-5.1.0.tar.gz
tar -xzvf apache-oozie-5.1.0.tar.gz
sudo mv apache-oozie-5.1.0 /opt/oozie
sudo chown -R oozie:oozie /opt/oozie
sudo nano /etc/profile
```



#### **Adicione as seguintes linhas ao final do arquivo:**

bash

```bash
export OOZIE_HOME=/opt/oozie
export PATH=$PATH:$OOZIE_HOME/bin
```



#### **Salve o arquivo e execute:**

bash

```bash
source /etc/profile
```



#### **Resultado:**

Você terá instalado e configurado um ecossistema de Big Data na nuvem usando o Hadoop, Spark, Hive, Pig e Oozie.





### Módulo 1: Introdução ao Ecossistema de Big Data na Nuvem



**Big Data** é um termo que descreve o grande volume de dados - estruturados e não estruturados - que inundam as empresas diariamente. Um ecossistema de Big Data na nuvem refere-se ao conjunto de tecnologias e ferramentas que permitem às organizações armazenar, processar e analisar esses dados em uma plataforma de nuvem.

**Exemplo Prático:** Uma empresa de e-commerce pode usar um ecossistema de Big Data na nuvem para analisar o comportamento de compra dos clientes, otimizar o gerenciamento de estoque e personalizar as recomendações de produtos em tempo real.

------

### Módulo 2: Componentes de um Ecossistema de Big Data na Nuvem



Um ecossistema de Big Data típico na nuvem inclui:

- **Armazenamento de Dados:** Serviços como Amazon S3 ou Google Cloud Storage.
- **Processamento de Dados:** Ferramentas como Apache Hadoop e Spark.
- **Análise de Dados:** Soluções como Google BigQuery ou Amazon Redshift.
- **Visualização de Dados:** Aplicações como Tableau ou Power BI.

**Exemplo Prático:** Utilizando o Apache Spark hospedado no AWS, uma empresa pode realizar análises complexas de dados de vendas para identificar tendências e padrões.

------

### Módulo 3: Melhorando o Algoritmo de Extração/Contabilização de Palavras



Para melhorar o algoritmo de extração e contabilização de palavras, podemos ordenar as palavras por ocorrência. Isso pode ser feito utilizando uma estrutura de dados chamada **mapa de frequência**, que contabiliza quantas vezes cada palavra aparece no texto.

**Exemplo de Código:**

```
from collections import Counter

def contar_palavras(texto):
    # Separar o texto em palavras
    palavras = texto.split()
    # Contar a frequência de cada palavra
    frequencia = Counter(palavras)
    # Ordenar as palavras pela frequência
    palavras_ordenadas = sorted(frequencia.items(), key=lambda item: item[1], reverse=True)
    return palavras_ordenadas

texto_exemplo = "big data big cloud data big cloud"
print(contar_palavras(texto_exemplo))
```



**Saída:**

```
[('big', 3), ('data', 2), ('cloud', 2)]
```



Este código Python utiliza a biblioteca `collections` para criar um contador que ajuda a contabilizar e ordenar as palavras por frequência de ocorrência, não por ordem alfabética.
