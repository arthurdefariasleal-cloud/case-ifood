# Case iFood - Otimização de Campanha de Marketing

# Estrutura do Projeto

```bash
case-ifood/
│
├── README.md
│
├── data/
│   ├── raw/
│   │   └── ifood_df.xlsx
│   │
│   └── processed/
│       └── analyze-case.xlsx
│
├── docs/
│   ├── iFood_Data_Analyst_Case.pdf
│   └── dictionary.png
│
└── images/
    ├── eda/
    │   ├── total_gasto.png
    │   ├── recencia.png
    │   ├── total_compras.png
    │   ├── idade.png
    │   ├── canal_compra.png
    │   └── estado_civil.png
    │
    └── study/
        ├── canal_x_aceitacao.png
        ├── estado_civil_aceitacao.png
        ├── recencia_x_aceitacao.png
        ├── ticket_x_aceitacao.png
        └── total_gasto_x_aceitacao.png
```

# Contexto
Este projeto foi desenvolvido a partir de um case técnico aplicado para uma vaga de Analista de Dados do iFood, disponível publicamente na plataforma Kaggle.

Ao encontrar este case, decidi conduzir um estudo de forma independente, com foco em explorar o problema de negócio, estruturar análises e propor uma solução acionável.

# Apresentação do Problema

O estudo aborda um case técnico de CRM Data Analyst do iFood, cujo desafio é otimizar campanhas de marketing a partir de dados históricos de clientes.

Uma campanha piloto foi realizada com 2.240 clientes selecionados aleatoriamente, visando a venda de um novo produto, mas o resultado gerou prejuízo financeiro. Diante teste cenário, o objetivo de negócio deste estudo é **identificar quais clientes devem ser priorizados na próxima campanha para maximizar o lucro**.

Para estruturar a análise, o problema foi modelado a partir do conceito de fato e dimensão, sendo a aceitação da campanha (Response) o fato central, enquanto variáveis comportamentais, monetária e de perfil as dimensões explicativas.

# Entendimento dos Dados

## Descrição da Base
A base original é composta por dados de clientes, reunindo perfil demográfico, comportamento de compra e engajamento com campanhas. Para transformar estes dados em análises, as variáveis foram organizadas em 3 categorias:

1. Perfil Demográfico - "Quem é o cliente"
2. Comportamento de Compra - "Como ele consome"
3. Engajamento com Marketing - "Como ele responde às campanhas"

<br>
<img width="391" height="739" alt="image" src="https://github.com/user-attachments/assets/ac01653e-2fbd-4c57-b80b-bd311161210b" />

## Análise Exploratória (EDA)
A EDA teve com objetivo compreender a composição da base antes de avanças para a análise. O foco aqui é identificar padrões, concentrações e possíveis viéses. 

Busquei explorar apenas variáveis que considerei mais representativas em diferentes dimensões do problema (comportamental, demográfica, operacionais e financeiras). Não houve a intenção de analisar todas as variáveis, mas de entender quem são os clientes, como compram e com que frequência compram, levantando hipóteses iniciais.

As análises de relação com a aceitação da campanha e a priorização de variáveis foram conduzidas em etapas posteriores por meio de métodos estatísticos.
<br><br>

<img width="1618" height="715" alt="image" src="https://github.com/user-attachments/assets/63fd1dc6-14cf-40f4-8f2a-a87442580bc8" />
<br><br>

Resumo da base:
* Familiar
* Madura
* De ticket médio baixo
* Dependente do canal físico
* Com parcela relevante inativa

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

## Fato (Response) x Dimensões
O estudo foi desenvolvido a partir da relação direta entre cada dimensão e a aceitação da campanha (Response). O objetivo foi quantificar diferenças de comportamento, identificar segmentos de maior probabilidade de conversão e preparar o terreno para a avaliação financeira da campanha.

### Total Gasto por Cliente (MnTotal)

<img width="648" height="349" alt="image" src="https://github.com/user-attachments/assets/49e08134-41d4-475f-b38f-808a4abd94cf" />
<br><br>

* Aceitação cresce exponencialmente com gasto histórico.
* Taxa cresce de 8% (R$0-100) para 45% (+R$1.500), mais de 5x maior.
* Trade-off entre volume e conversão: maior volume concentrado nas faixas de menor gasto e maior conversão nas faixas maiores.
* Clientes de alto gasto + maior chance de resposta -> maior lucro por contato.

### Ticket Médio

<img width="644" height="348" alt="image" src="https://github.com/user-attachments/assets/0b640d48-9ec0-4d9e-b4b7-918b82af23ef" />
<br><br>

* Aumento expressivo na taxa de aceitação à medida que o ticket médio cresce.
* Trade-off entre volume e conversão: maior volume concentrado na faixa de baixo ticket médio e maior conversão na faixa de alto ticket médio.
* Clientes de alto ticket médio + maior chance de resposta -> maior lucro por contato.

### Recência de Compras

<img width="646" height="348" alt="image" src="https://github.com/user-attachments/assets/23111646-d428-454e-bcdd-5ef5b1a3ec87" />
<br><br>

* Queda consistente de aceitação à medida que o tempo desde a última compra aumenta.
* Clientes com recência de até 15 dias têm 30% de aceitação (2x a média geral de aceitação)
* Clientes com recência de 16-45 dias têm aceitação próxima a media geral. A partir do 46º dia observa-se uma queda consistente até chegar em 7% (99 dias).

### Canal de Compra

<img width="648" height="347" alt="image" src="https://github.com/user-attachments/assets/6b894b22-ab07-42a1-8a7a-80d771fae5b7" />
<br><br>

* Catalog apresenta a maior eficiência em aceitação.
* Trade-off muito forte entre Catalog e Store: volume x aceitação.
* Store concentra escala, mas tem baixa aceitação (10%)

### Estado Civil

<img width="648" height="351" alt="image" src="https://github.com/user-attachments/assets/32799336-292f-46c1-989d-478d3e44632a" />
<br><br>

* Solteiros e viúvos convertem 2x mais que casados e juntos.
* Casados e juntos concentram mais de 60% da base, reduzindo o sucesso da campanha.
* Trade-off entre volume e aceitação nas categorias Solteiro/Viúvos e Casados/Juntos

**Resumos dos insights:**
* A aceitação da campanha é concentrada em clientes de maior valor e maior engajamento (alto gasto histórico, ticket médio alto e baixa recência).
* Padrão consistente de trade-off entre volume e eficiência em todas as dimensões (canal, estado civil, gasto total e ticket médio)
* A decisão deve ser orientada por lucro esperado por segmento.

## Segmentação
Nesta etapa do estudo, os clientes foram segmentos de acordo com recência, gasto total e ticket-médio. Para cada segmento, foram calculados o total de clientes contactados, aceitação da campanha e o lucro esperado. 

Ao final, o modelo resultou em um conjunto claro e segmentos prioritários para o alvo da campanha.

# Avaliação dos Resultados (Cenário Pré x Cenário Pós Estudo)
Nesta etapa, comparo o desempenho financeiro da campanha piloto (pré-estudo) com o cenário pós-estudo.

A campanha piloto apresentou uma taxa média de conversão de 15% e um prejuízo financeiro de R$ 3.046,00. Esse valor foi calculado com base nos dados de Custo Total da Campanha e Receita Total Gerada informados na apresentação do problema. Veja abaixo:

### Pré-Estudo
Dados Primários:
* Clientes da campanha piloto: 2240
* Custo total da campanha: R$ 6.720,00
* Receita total gerada: R$ 3.674,00
* Taxa de sucesso (aceitação): 15%
* Lucro da campanha: -R$ 3.046,00

### Pós-Estudo (Estratégia Proposta)
Com a segmentação, observou-se que apenas uma parcela específica da base gera lucro positivo esperado.  Essa parcela é caracaterizada por clientes com baixa recência e com maior valor econômico. A exclusão dos segmentos não lucrativos reduz significativamente o custo total da campanha e melhora a eficiência do investimento, com um lucro estimado de R$ 569,49.
<br><br>

<img width="1122" height="310" alt="image" src="https://github.com/user-attachments/assets/8a49b0fb-f221-4c6e-8f97-6a7a76276f4a" />
<br><br>

A comparação entre os dois cenários mostra que o insucesso da campanha está no fato dele ser massificada, sem segmentação.

A estratégia adotada transforma uma campanha deficitária em uma ação economicamente lucrativa, ainda que em pequena escala. Dessa forma, a expansão desta campanha dentro dos segmentos recomendados tende a aumentar o lucro esperado, desde que os custos sejam os mesmos.

A segmentação por Canal de Venda foi utilizada como refinamento da decisão, aplicando apenas aos segmentos já considerados lucrativos. A análise mostrou que Catalog e Web apresentam maior retorno com melhor relação entre receita esperada e custo de campanha. Já o canal, Store, apesar de gerar receita, possui menor lucro. Assim, os canais Catalog e Web devem ser priorizados sempre que possível, sendo Store utilizado como um canal complementar.
<br>

<img width="620" height="85" alt="image" src="https://github.com/user-attachments/assets/f1a345b6-78d8-445a-9ced-1318406abcf8" />

# Conclusão e Recomendações Acionáveis

## Problema identificado
A campanha piloto, enviada de forma massificada, apresentou prejuízo financeiro, demonstrando que a taxa média de aceitação não gera lucro.

## O que a análise revelou
Adaptar a campanha para segmentos específicos gera lucro. Esses segmentos são caracterizados por:
* Alta recência;
* Maior gasto histórico;
* Ticke Médio elevado.

## Recomendações de Negócio
### 1. Recência de Compra
* Priorizar clientes que fizeram sua última compra há pouco tempo (até 30 dias)
* Estender recência até 45 dias apenas para clientes de alto valor gasto (>= R$ 1.500,00 ou ticket médio >= +R$ 50,00).
* Evitar realizar a campanha com clientes com recência superior a 45 dias.

### 2. Total Gasto (MnTotal)
* Utilizar Gasto Total como critério central da campanha.
* Direcionar a campanha para clientes com alto gasto histórico, especialmente a partir das faixas superiores.

### 3. Ticket Médio
* Priorizar clientes com ticket médio elevado, especialmente acima de R$50.
* Utilizar Ticket Médio como filtro adicional: alto ticket + alta recência = segmento prioritário

### 4. Canal de Compra
* Priorizar os canais Web e Catalog na execução da campanha.
* Utilizar canal Store de forma complementar.

