# Rota Inteligente: Otimização de Entregas da Sabor Express com Algoritmos de IA 

### Feito por: Rafael Silva 100788

### Link do Colab (abra e faça uma cópia): [https://colab.research.google.com/drive/13NXAVl2g6UCmmNhda7A3wj1zFDlI5XDb?usp=sharing](https://colab.research.google.com/drive/13NXAVl2g6UCmmNhda7A3wj1zFDlI5XDb?usp=sharing)

## Descrição do Projeto
Este projeto apresenta uma solução de **otimização de entregas** para a empresa fictícia **Sabor Express**, uma companhia local de delivery que enfrenta dificuldades para gerenciar suas rotas em horários de pico.  
O objetivo é desenvolver um sistema inteligente que encontre **as melhores rotas de entrega**, reduzindo atrasos e custos, e aumentando a satisfação dos clientes.

O projeto foi desenvolvido como parte da disciplina **Artificial Intelligence Fundamentals**, aplicando algoritmos clássicos de IA em um problema realista de logística.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Objetivo e Desafio
O desafio consiste em:
- Representar a cidade como um **grafo**, onde os nós são pontos de entrega e as arestas representam ruas com pesos baseados em tempo e distância.
- Implementar algoritmos de busca (A\* + K-means) para encontrar **rotas ideais entre múltiplos pontos**.
- Aplicar **clustering (K-Means)** para agrupar entregas em zonas eficientes.
- Avaliar o desempenho e gerar um **relatório de entrega com métricas e satisfação de clientes**.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Abordagem e Algoritmos Utilizados

###  Representação com Grafos
A cidade foi modelada como um **grafo não direcionado**, onde:
- Cada **nó** representa uma coordenada (casa, rua ou cliente).
- Cada **aresta** possui um peso (`time_min`) indicando o tempo estimado para percorrer o trecho.
- Foram criadas duas versões de grafo:
  - `graph_edges.csv` — cenário normal.
  - `graph_edges_transito.csv` — cenário com trânsito pesado (5x mais tempo em vias específicas do centro).

###  Algoritmo A\*
O A\* é utilizado para encontrar o **menor caminho entre dois pontos** com base em uma heurística (distância euclidiana).  
Ele é responsável por calcular:
- Rotas entre loja e clientes.
- Custos totais das rotas dentro de cada cluster.

###  Agrupamento com K-Means
As entregas são agrupadas em **zonas inteligentes**, considerando as **distâncias reais do grafo** (calculadas com Dijkstra).  
Para evitar distorções visuais, foi utilizado o **MDS (Multidimensional Scaling)** para transformar as distâncias em um espaço 2D e usar o K-Means.

###  HORA DA ENTREGA
O sistema aplica uma heurística adaptativa:
a cada passo, o entregador é direcionado ao ponto mais próximo considerando o mapa real do grafo.
Essa decisão local, repetida até o fim da rota, gera resultados próximos do melhor em segundos, perfeito para situações com muitos pedidos e necessidade de resposta imediata.

---

## 8) Estrutura do projeto
```
 rota-inteligente/
│
├──  data/
│ ├── graph_edges.csv
│ ├── graph_edges_transito.csv
│ ├── nodes.csv
│ ├── orders.csv
│ └── relatorio_entregas.csv
│
├──  src/
│ └── main.ipynb # notebook com o código completo
│
└── README.md
```

## Execução (Passo a Passo no Google Colab)

1 - abra o - `rota_inteligente.ipynb` 

2 - crie uma pasta -`data` 

3 - faça o upload dos arquivos nesta pasta - `graph_edges.csv` - `graph_edges_transito.csv` - `nodes.csv` - `orders.csv`

deve ficar assim dentro do colab:

```
Arquivos
│
├──  data/
│ ├── graph_edges.csv
│ ├── graph_edges_transito.csv
│ ├── nodes.csv
│ ├── orders.csv
```

### após isso, execulte as células na ordem. 

Parte 1 — Instalação e importação das bibliotecas
(pandas, networkx, matplotlib, sklearn, tqdm, numpy)

Parte 2 - Carregamento dos Dados e Visualização do Grafo

Parte 3 - Implementação do A*

Parte 4 - Téste do A*

Parte 5 - Pondo em prática o algoritimo A*

Parte 6 - Agrupamento de entregas com o K-Means (Zonas de entrega)

Parte 7 - A* + K-means (melhores rotas)

Final - Relatorio de entrega por entregador/cluster

### No final da execução, você verá:

O mapa do grafo com as zonas coloridas (clusters de entrega)

As rotas ideais de cada entregador (A*)

O relatório de desempenho das entregas com emojis de satisfação
