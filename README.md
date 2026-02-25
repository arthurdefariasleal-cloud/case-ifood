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

<img width="391" height="739" alt="image" src="https://github.com/user-attachments/assets/ac01653e-2fbd-4c57-b80b-bd311161210b" />

## Análise Exploratória (EDA)
A EDA teve com objetivo compreender a composição da base antes de avanças para a análise. O foco aqui é identificar padrões, concentrações e possíveis viéses. 

Busquei explorar apenas variáveis que considerei mais representativas em diferentes dimensões do problema (comportamental, demográfica, operacionais e financeiras). Não houve a intenção de analisar todas as variáveis, mas de entender quem são os clientes, como compram e com que frequência compram, levantando hipóteses iniciais.

As análises de relação com a aceitação da campanha e a priorização de variáveis foram conduzidas em etapas posteriores por meio de métodos estatísticos.
<br><br>

<img width="1618" height="715" alt="image" src="https://github.com/user-attachments/assets/63fd1dc6-14cf-40f4-8f2a-a87442580bc8" />
<br><br>

Resumo da base + insights:
* Familiar
* Madura
* De ticket médio baixo
* Dependente do canal físico
* Com parcela relevante inativa

## Hipóteses de Negócio
1. Clientes mais recentes devem apresentar maior propensão a resposta.
2. Clientes de maior gasto acumulado devem concentrar maior taxa de aceitação.
3. Canais digitais podem apresentar melhor desempenho para campanhas.
4. Perfis familiares podem responder melhor à campanha.

# Preparação dos Dados
Esta etapa envolveu:
* Validação de tipos e consistências das variáveis.
* Criação de métricas derivadas (ex.: id, ticket médio, total de compras, canal predominante, estado civil).
* Construção de faixas (binning) para variáveis contínuas.
* Tratamento de outiliers e amostras de baixo volume.
* Definição explícita de fato, dimensões e variável-alvo.

# Modelagem
## Método Estatístico para Priorização das Variáveis

As variáveis foram selecionadas com base no método estatístico Information Value (IV), com o objetivo de priorizar aquelas com poder de separação forte e moderado. 

A variável Total de Compras foi excluída da análise por apresentar uma redundância conceitual com Ticket Médio e Total Gasto (MnTotal), sendo estas mantidas por representarem o valor econômico do cliente.

<img width="625" height="362" alt="image" src="https://github.com/user-attachments/assets/cf639e1c-7578-4e7e-8656-56d56a604ca1" />


## Desenvolvimento do Estudo
O estudo foi desenvolvido a partir da relação direta entre cada dimensão e a aceitação da campanha (Response). O objetivo foi quantificar diferenças de comportamento, identificar segmentos de maior probabilidade de conversão e preparar o terreno para a avaliação financeira da campanha.

### Total Gasto por Cliente (MnTotal)

<img width="650" height="390" alt="image" src="https://github.com/user-attachments/assets/362a81ab-0bbf-4ea9-87f4-38bd38bcb202" />
<br><br>

* Aceitação cresce exponencialmente com gasto histórico.
* Clientes com maior valor histórico de gasto respondem melhor à campanha.

### Ticket Médio

<img width="644" height="348" alt="image" src="https://github.com/user-attachments/assets/0b640d48-9ec0-4d9e-b4b7-918b82af23ef" />
<br><br>

* Aumento expressivo na taxa de aceitação à medida que o ticket médio cresce.
* Clientes com ticket médio mais elevado, ainda que em menor volume, tendem a converter mais.

### Recência de Compras

<img width="646" height="348" alt="image" src="https://github.com/user-attachments/assets/23111646-d428-454e-bcdd-5ef5b1a3ec87" />
<br><br>

* Aumento expressivo na taxa de aceitação à medida que o ticket médio cresce.
* Clientes com ticket médio mais elevado, ainda que em menor volume, tendem a converter mais.

### Canal de Compra

<img width="648" height="347" alt="image" src="https://github.com/user-attachments/assets/6b894b22-ab07-42a1-8a7a-80d771fae5b7" />
<br><br>

* Trade-off entre volume e taxa de aceitaçãopesar do maior volume.
* Store concentra a maior parte dos clientes, porém os canais Catalog e Web apresentam maiores taxas de resposta.
* Maior volume compensa menor taxa de aceitação?

### Estado Civil

<img width="648" height="351" alt="image" src="https://github.com/user-attachments/assets/32799336-292f-46c1-989d-478d3e44632a" />
<br><br>

* Perfis não familiares parecem mais sujeitos à aceitação.
* Casados e "juntos" representam mais da metade da base (65%), mas apresentam baixa taixa de aceitação.



