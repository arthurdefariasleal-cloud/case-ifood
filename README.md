# case-ifood
Otimização de Campanha de Marketing - Identificando clientes com maior potencial de retorno financeiro.

# Contexto
Este projeto foi desenvolvido a partir de um case técnico aplicado para uma vaga de Analista de Dados do iFood, disponível publicamente na plataforma Kaggle.

Ao encontrar este case, decidi conduzir um estudo de forma independente, com foco em explorar o problema de negócio, estruturar análises e propor uma solução acionável.

# Apresentação do Problema

O estudo aborda um case técnico de CRM Data Analyst do iFood, cujo desafio é otimizar campanhas de marketing a partir de dados históricos de clientes.

Uma campanha piloto foi realizada com 2.240 clientes selecionados aleatoriamente, visando a venda de um novo produto, mas o resultado gerou prejuízo financeiro. Diante teste cenário, o objetivo de negócio deste estudo é **identificar quais clientes devem ser priorizados na próxima campanha para maximizar o lucro**.

Para estruturar a análise, o problema foi modelado a partir do conceito de fato e dimensão, sendo a aceitação da campanha (Response) o fato central, enquanto variáveis comportamentais, monetária e de perfil as dimensões explicativas.

# Entendimento dos Dados

## Descrição da Base
A base original é composta por dados de clientes, reunindo perfil demográfico, comportamento de compra e engajamento com campanhas. 

Para transformar estes dados em análises, as variáveis foram organizadas em 3 categorias:

1. Perfil Demográfico - "Quem é o cliente"
2. Comportamento de Compra - "Como ele consome"
3. Engajamento com Marketing - "Como ele responde às campanhas"

### 1. Perfil Demográfico (Quem é o cliente)
**Dados socioeconômicos:**
* Income
* Age

**Estrutura Familiar:**
* Kidhome
* Teenhome

**Estado Civil:**
* maritial_Divorced
* marital_Married
* marital_Single
* marital_Together
* marital_Widow

**Escolaridade:**
* education_2n Cycle
* education_Basic
* education_Graduation
* education_Master
* education_PhD

### 2. Comportamento de Compra (Como ele consume)
**Recência e relacionamento:**
* Recency
* Customer_Days

**Gasto por categorias:**
* MntWines
* MntFruits
* MntMeatProducts
* MntFishProducts
* MntSweetProducts
* MntGoldProds

**Variáveis agregadas de gasto:**
* MntTotal
* MntRegularProds

**Frequência de compra por canal:**
* NumDealsPurchases
* NumWebPurchases
* NumCatalogPurchases
* NumStorePurchases

**Engajamento Digital:**
* NumWebVisitMonth

### 3. Engajamento com Marketing
**Histórico de campanhas:**
* AcceptedCmp1
* AcceptedCmp2
* AcceptedCmp3
* AcceptedCmp4
* AcceptedCmp5
* AcceptedCmpOverall

**Target principal:**
* Response

**Satisfação:**
* Complain

## Análise Exploratória (EDA)
A EDA teve com objetivo compreender a composição da base antes de avanças para a análise. O foco aqui é identificar padrões, concentrações e possíveis viéses. 

Busquei explorar apenas variáveis que considerei mais representativas em diferentes dimensões do problema (comportamental, demográfica, operacionais e financeiras). Não houve a intenção de analisar todas as variáveis, mas de entender quem são os clientes, como compram e com que frequência compram, levantando hipóteses iniciais.

As análises de relação com a aceitação da campanha e a priorização de variáveis foram conduzidas em etapas posteriores por meio de métodos estatísticos.

<img width="1618" height="715" alt="image" src="https://github.com/user-attachments/assets/63fd1dc6-14cf-40f4-8f2a-a87442580bc8" />

