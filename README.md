# Insurance-Cross-Sell
## 1. Contextualização
Uma apólice de seguro é um acordo pelo qual uma empresa se compromete a fornecer uma garantia de indenização por perda, dano, doença ou morte especificada em troca do pagamento de um valor específico. 

No contexto deste projeto, temos uma seguradora, que é especializada em apólices de seguro-saúde e quer saber, quais dos seus clientes, tem o interesse em adquirir também o seguro para veículos.

Construir um modelo para prever se um cliente estaria interessado em Seguro de Veículo é extremamente útil para a empresa, pois ela pode planejar sua estratégia de comunicação para alcançar esses clientes e otimizar seu modelo de negócios e receita.

## 2. Problema de negócio
Como a empresa em questão, possui um time reduzido de vendas, inicialmente o contato será preferencialmente para 20.000 clientes. 
O objetivo do projeto é construir um modelo de Machine Learning, que consiga oferecer uma lista ordenada, rankeando os clientes por um score (decrescente), 
indicando quais os clientes tem a maior probabilidade de adquirir o seguro para veículos.

## 3. Planejamento da solução
Antes de iniciar o projeto, foi feito o planejamento da solução, onde foram traçadas as estratégias para atender cada necessidade para a execução das etapa do projeto: o produto final que será entregue, as ferramentas necessárias e o processo para atingir os resultados esperados.

### 3.1 Produto final
A entrega será feita através de um relatório, contendo um ranking com o id do cliente e o seu score, a partir de uma classificação decrescente.
Também será oferecido um Dashboard Interativo com as principais métricas de avaliação dos clientes.

### 3.2 Ferramentas
* Pandas
* Python
* Git e GitHub
* VSCode
* Algoritmos de classificação
* Bibliotecas de Machine Learning SKLearn
* StreamLit

### 3.3 Processo: Estratégia para a solução do problema de negócio 
A construção da solução foi esquematizada dentro da Metodologia de desenvolvimento de projetos CRISP, que é baseada em ciclos, potencializando a organização e velocidade na entrega de resultados. Os ciclos estão organizados nas seguintes etapas:

a) Entendimento da questão de negócio, discussão dos pontos relevantes e possíveis dúvidas com o time de negócio, retratando as particularidades a serem atendidas no projeto.

b) Coleta de dados: Os dados serão coletados no formato .csv e divididos em treino (treino + validação) e teste. Para este projeto de estudo, o dataset utilizado foi proveniente da Plataforma Kaggle

c) Descrição dos dados: Noção de quantidade de dados, tipos de variáveis, estatística descritiva das variáveis numéricas e análise de variáveis categóricas.

d) Limpeza: drop ou substituição de valores nulos ou faltantes.

e) Feature engineering: Criação e derivação de novas variáveis

f) Análise exploratória de dados(EDA): O objetivo da EDA é gerar insights a partir da análise de hipóteses e ter uma ideia das melhores variáveis para a modelagem de dados e a correlação entre elas. Essa etapa inicia na construção de um mapa de hipóteses (MindMap) com o objetivo de levantar hipóteses sobre as variáveis que influenciam o fenômeno de vendas. As análises são distribuídas em Univariada, Bivariada e Multivariada.

g) Preparação dos dados: Transformação das variáveis de interesse (melhorar a performance do modelo.

h) Seleção de features: escolher as features mais relevantes para a aprendizagem do modelo.

i) Modelo de Machine Learning: O problema de negócio, é um tipo de problema de classificação (classificar quais clientes estão interessados no produto). A solução proposta visa a previsão de um ranking (Ranking to Learn), ordenando os clientes através de um score (do mais interessado ao menos interessado). O propósito é encontrar os 20.000 clientes mais interessados no novo produto, visto que o time de vendas tem uma possibilidade de contato limitada. Os algoritmos treinados serão mensurados a partir de Curvas de Ganho (Cumulative Gain) e Lift.

j) Resultados: Os resultados poderão ser acessados através de um Dashbnorad interativo, construído com a ferramenta StreamLit.

## 4. Principais insights observados a partir da análise das hipóteses:
* H01 - Homens e mulheres tem o mesmo interesse em adquirir o seguro de veículos: A hipótese é falsa, de acorod com os dados da base, homens tem mais interesse em aquirir o seguro. 
img1

* H02 - Clientes que já sofreram algum tipo de dano em seu carro, tem mais interesse em adquirir um seguro de carro A hipótese é verdadeira, observa-se uqe 97.9% das pessoas interessadas já sofreram algum tipo acidente no seu carro.
img2

* H3 - Clientes que possuem carros mais novos, tem mais interesse em comprar o seguro de carro: A hipótese é verdadeira, pois 89.9% dos interessados, possuem carros mais novos.
img3

* H4 - Apenas as pessoas que possuem carteira de motorista tem interesse em seguro de carro. A hipótese é falsa, porque, apesar de ser em uma pequena proporção, não é possível afirmar que todas as pessoas que não tem carteira de motorista também não querem o seguro de carro.
img4

* H5 - A idade do cliente influencia o interesse em seguro de carro: A hipótese é verdadeira. Podemos observar que existe uma faixa de maior interesse, em adquirir o seguro, de carro de 30 a 60 anos.
img5

## 5. Resultado dos modelos de Machine Learning
Após o treinamento dos modelos, observou-se a sua performance através das métricas Recall@k e Precision@k, comparados a partir do método do CrossValidation:

img6

O modelo escolhido foi o LGBM, por apresentar a melhor performance.
A sua capacidade de generalização, ou seja, a classificação de dados inéditos, foi medida pela Curve Cumulative Gain e Lift.
Considerando as 20.000 primeiras ligações, observa-se que utilizar o modelo para fazer a escolha dos clientes interessados em adquirir o seguro, é 2.2 vezes melhor que escolher de forma aleatória.  
Em 26% da base, o modelo acerta em 55% os clientes interessados.

img7

img8

Ainda, ao utilizar 65,65% dos dados de validação, o que se traduziria em 40 mil ligações realizadas pela equipe de vendas, o modelo seria capaz de identificar 99,9% de pessoas do total de interessados em adquirir o seguro.

img9

img10

## 6. Conversão dos resultados para o Produto Financeiro
Considerando uma amostra de 127.000 novos clientes, para rankeamento de score e a realização de 20.000 ligações, escolher de forma aleatória significaria acertar 33%, enquanto o  modelo acerta 81%. Ainda, considerando uma receita mensal por cliente de R$2.000, a diferença entre a receita anual da escolha aleatória e a escolha sugerida pelo modelo é de R$ 1.463.040.000.

img11

## 7. Conclusão
As metas do projeto foram atingidas, a partir da construção de um modelo, capaz de ordenar os clientes em uma lista a partir de seu score, possibilitando ao time de vendas realizar as ligações de forma mais assertiva e eficiente, economizando tempo e recursos.

img12

## 8. Próximos passos
* Criar o DashBoard com os resultados no StreamLit.
* Aplicar o finetunning para descobrisa parâmetros melhores para as features de treinamento do modelo.
* Deploy do modelo.

## 9. Referências
* Este projeto é baseado em um problema de negócio fictício, construído junto à Comunidade DS, como Projeto do Aluno 004 (PA004), onde cada aluno constrói a sua proposta de solução para o problema.
* O dados forma coletados na plataforma Kaggle.
* As imagens utilizadas são do meu acervo pessoal.
