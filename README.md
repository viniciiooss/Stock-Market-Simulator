# Projeto de Análise e Processamento de Dados do S&P 500 com Kafka e AWS

Este projeto demonstra um pipeline de ingestão, processamento e análise de dados financeiros usando Apache Kafka e diversos serviços da AWS, como Glue, Athena, EC2 e S3. O objetivo principal é coletar dados do mercado financeiro (S&P 500), processá-los em tempo real e disponibilizá-los para consultas e análises.

## 🗂 Visão Geral

O pipeline de dados foi desenvolvido para capturar informações do mercado financeiro, armazená-las no Kafka e realizar transformações utilizando ferramentas como o AWS Glue. Os dados processados são armazenados no Amazon S3 e podem ser consultados utilizando o AWS Athena. Um Jupyter Notebook foi utilizado para explorar, visualizar e analisar os dados.

## ⚙️ Arquitetura do Projeto

Componentes Principais
- Apache Kafka:
Usado para ingestão e processamento de dados em tempo real.
O notebook KafkaProducer.ipynb envia os dados de mercado para o Kafka.
O notebook KafkaConsumer.ipynb consome os dados e os armazena em uma estrutura apropriada para processamento.
- AWS Glue:
Utilizado para realizar o ETL (Extração, Transformação e Carga) dos dados do S3 para preparação e catalogação.
- AWS S3:
Armazenamento dos dados brutos e transformados.
- AWS Athena:
Realiza consultas SQL nos dados armazenados no S3, facilitando a análise e geração de relatórios.
- AWS EC2:
Hospeda o servidor Kafka e gerencia a comunicação entre produtores e consumidores.
- Jupyter Notebook:
Utilizado para desenvolver scripts de ingestão e consumo de dados, assim como para análises exploratórias e visualizações dos resultados.
## 🗃️ Dados Utilizados

O projeto utiliza um conjunto de dados históricos do S&P 500 (sp500_data_2021_to_2024.csv) que contém informações financeiras de 2021 a 2024. As informações são atualizadas em tempo real e enviadas ao Kafka, onde são processadas e disponibilizadas para consulta no Athena.

## 🔧 Passos de Configuração

- Configuração do Kafka:
Configuração de tópicos para envio e consumo de dados.
Definir a estrutura dos dados para serem processados pelo consumidor.
- Configuração dos Serviços AWS:
Criar buckets no S3 para armazenamento dos dados brutos e processados.
Definir Glue Crawlers para catalogar os dados e criar tabelas.
Criar consultas no Athena para acessar os dados transformados.
- Execução dos Notebooks:
KafkaProducer.ipynb: Responsável por enviar dados para o Kafka.
KafkaConsumer.ipynb: Consome os dados do Kafka e realiza transformações básicas.
## 📊 Consultas no Athena

A partir das imagens fornecidas, foram executadas as seguintes consultas no AWS Athena:

Consulta de contagem de registros:
```bash
SELECT COUNT(*) FROM "stock-market-kafka"."kafka_stock_sp500" LIMIT 10;
```
Resultado: 226 registros.

Consulta da última data no dataset:
```bash
SELECT MAX(DATE) FROM "stock-market-kafka"."kafka_stock_sp500" LIMIT 10;
```

Resultado: Data mais recente — 2024-09-25.
Essas consultas confirmam a eficácia do pipeline de dados para armazenar e consultar informações atualizadas do mercado financeiro.

## 🚀 Execução

Para executar o projeto, siga as etapas descritas nos notebooks (KafkaProducer.ipynb e KafkaConsumer.ipynb) e consulte os dados no Athena conforme as queries fornecidas. Certifique-se de que todas as dependências estejam configuradas corretamente e os serviços AWS estejam em execução.

## 📈 Resultados

Ingestão de Dados em Tempo Real: Os dados do mercado financeiro são capturados em tempo real e processados pelo pipeline.
Armazenamento Eficiente: Dados armazenados no S3 e consultáveis via Athena.

## 📜 Licença

Este projeto está licenciado sob os termos da licença MIT.
