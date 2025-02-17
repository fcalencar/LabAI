# LabAI

## Criação do ML automatizado

Acessar **+ Novo trabalho de ML automatizado**

Usar as informação abaixo para criação do trabalho de ML automatizado e avançar conforme necessário.

**1. Método de treinamento:**

Escolha o método de treinamento **Treinar automaticamente**.

**2. Configurações básicas:**

**Nome do trabalho:** Mantenha-o como está.\
**Novo nome do experimento:** mslearn-bike-rental\
**Descrição:** Aprendizado de máquina automatizado para previsão de aluguel de bicicletas\
**Tags:** nenhuma

**3. Tipo de tarefa e dados:**

**Selecione o tipo de tarefa:** Regressão

**Selecionar os dados:**

Acessar + Criar

**3.1. Tipo de dados:**

**Nome:** bike-rentals\
**Descrição:** Historic bike rental data\
**Tipo:** Tabela (mltable)

**3.2. Fonte de dados:**

**Selecione:** De arquivos locais

**3.3. Tipo de armazenamento de destino :**

**Tipo de armazenamento de dados:** Azure Blob Storage\
**Nome:** workspaceblobstore

**3.4. Seleção de MLtable**

Acessar Carregar pasta

**Carregar os arquivos abaixo:**
 - daily-bike-share.csv
 - MLTable

Selecione **Criar**. Após a criação do conjunto de dados, selecione o conjunto de dados bike-rentals para continuar a enviar o trabalho de ML automatizado.

**4. Configurações de tarefas:**

**Tipo de tarefa:** Regressão\
**Conjunto de dados:** bike-rentals\
**Coluna de destino:** rentals (Integer)

**Configurações adicionais:**

**Métrica primária:** NormalizedRootMeanSquaredError\
**Explique o melhor modelo:** Não selecionado\
**Habilitar empilhamento de conjunto:** Não selecionado\
**Usar todos os modelos suportados:** Não selecionado\
**Modelos permitidos:** Selecione apenas RandomForest e LightGBM.

**Limites:**

**Máximo de avaliações:** 3\
**Máximo de avaliações simultâneos:** 3\
**Máximo de nós:** 3\
**Limite de pontuação métrica:** 0.085\
**Tempo limite do experimento:** 15\
**Tempo limite de iteração:** 15\
**Habilitar encerramento antecipada:** Selecionado

**Validação e teste:**

**Tipo de validação:** Divisão de validação de treinamento\
**Porcentagem de dados de validação:** 10\
**Conjunto de dados de teste:** Nenhum

**Computação:**

**Selecione o tipo de computação:** Sem servidor\
**Tipo de máquina virtual:** CPU\
**Camada de máquina virtual:** Dedicada\
**Tamanho da máquina virtual:** Standard_DS3_V2\
**Número de instâncias:** 1

## Implantar e testar o modelo

1. Na guia Modelo, selecione **Implantar**, use a opção **Terminal em tempo real**.

**Contagem de instâncias:** 3\
**Máquina virtual:** Standard_DS3_v2\
**Ponto final:** Novo\
**Nome do ponto de extremidade:** Deixe o padrão\ 
**Nome da implantação:** Deixe o padrão\
**Inferência de coleta de dados:** Desativado\
**Modelo de pacote:** Desativado

Aguarde até que o Implantar status para Deploy 

## Teste o serviço implantado

Acessar **Ponto de extremidade** no menu lateral e selecione o ponto de extremidade.\
Selecione **Testar**

**Input:**
```json
{
  "input_data": {
    "columns": [
      "day",
      "mnth",
      "year",
      "season",
      "holiday",
      "weekday",
      "workingday",
      "weathersit",
      "temp",
      "atemp",
      "hum",
      "windspeed"
    ],
    "index": [0],
    "data": [[1,1,2022,2,0,1,1,2,0.3,0.3,0.3,0.3]]
  }
 }
```
Clicar no botão **Testar**.

**Output**
```json
[
    335.75521469847945
]
```
