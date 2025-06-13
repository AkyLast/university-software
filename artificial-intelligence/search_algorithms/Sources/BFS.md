# 🧠 Busca em Largura (BFS) — Aprofundamento Total

---

## 🎯 Objetivo da BFS

Explorar **todos os caminhos possíveis em largura**, começando da raiz (estado inicial), expandindo **nível por nível**, até encontrar:

- O estado objetivo (`goal`)
    
- Ou **todos os caminhos mínimos** até um certo nível
    

---

## 🌊 Como ela "pensa":

Imagine um rio que se expande para todos os lados ao mesmo tempo. Ele visita todos os vizinhos do primeiro nível antes de prosseguir para os próximos níveis.

---

## 📦 Estruturas de Dados

|Estrutura|Finalidade|
|---|---|
|**Fila (queue)**|Armazena os nós que serão expandidos em ordem FIFO|
|**Visitados (set/list)**|Garante que nenhum estado será expandido duas vezes|
|**Pais / Caminho**|Guarda de onde cada estado veio, para reconstruir o caminho|

---

## 🔁 Passo a Passo do Algoritmo

```python
from collections import deque

def bfs(start, goal, get_neighbors):
    fila = deque()
    fila.append([start])  # cada item é um caminho, não só um nó!
    visitados = set()
    visitados.add(start)

    while fila:
        caminho = fila.popleft()
        no_atual = caminho[-1]

        if no_atual == goal:
            return caminho  # Caminho encontrado!

        for vizinho in get_neighbors(no_atual):
            if vizinho not in visitados:
                visitados.add(vizinho)
                novo_caminho = caminho + [vizinho]
                fila.append(novo_caminho)

    return None  # Se não encontrar
```

---

## ✅ Propriedades da BFS

|Propriedade|Valor|
|---|---|
|**Completa**|✔️ Sim (se o grafo for finito)|
|**Ótima**|✔️ Sim (se custo uniforme entre arestas)|
|**Tempo**|O(bd)O(b^d)|
|**Espaço**|O(bd)O(b^d)|
|**Tipo de Busca**|Cega (não usa heurística)|

- `b`: fator de ramificação (número médio de vizinhos por nó)
    
- `d`: profundidade da solução mais rasa
    

---

## 🧠 Comparação com outras buscas

| Algoritmo | Ordem de expansão  | Ótima? | Precisa de Heurística? |
| --------- | ------------------ | ------ | ---------------------- |
| BFS       | Nível por nível    | ✔️     | ❌                      |
| DFS       | Profundidade total | ❌      | ❌                      |
| [[UCS]]   | Menor custo total  | ✔️     | ❌                      |
| [[A*]]    | Custo + heurística | ✔️     | ✔️                     |

---

## 📊 Simulação Gráfica da Expansão (Grade 3x3):

```
(1,1) - (1,2) - (1,3)
  |       |       |
(2,1) - (2,2) - (2,3)
  |       |       |
(3,1) - (3,2) - (3,3)
```

### Caminho BFS de (1,1) até (3,3):

Ordem de visita:

```
[(1,1)], [(1,2), (2,1)], [(1,3), (2,2), (3,1)], ...
```

Ele **não pega o mais direto**. Ele explora todos os caminhos de mesmo comprimento primeiro.

---

## 📎 Aplicações Reais da BFS

|Aplicação|Uso|
|---|---|
|Resolução de labirintos|Encontrar caminhos curtos|
|Web Crawlers|Explorar links por nível|
|Problemas de jogos tabuleiro|Encontrar menor sequência de jogadas|
|Redes sociais|Encontrar amigos em comum, graus de separação|

---

## 🎮 Mini-Desafio (nível 1):

> Considere o grid abaixo. As células com “X” são bloqueadas:

```
S . .
X X .
. . G
```

- S = Start = (0,0)
    
- G = Goal = (2,2)
    

1. Simule **manualmente** a BFS
    
2. Liste a ordem de visita dos nós
    
3. Qual é o caminho encontrado?
    

Posso corrigir seu resultado depois se quiser 🧠

---

## 🔍 Deseja agora:

1. Resolver esse mini-desafio?
    
2. Ver como BFS se adapta para grafos com ciclos?
    
3. Aprender a **visualizar BFS passo a passo** com grafo?
    
4. Comparar com DFS na prática?
    

---
# 🧠 Busca em Largura (BFS) — Aprofundamento Total

---

## 🎯 Objetivo da BFS

Explorar **todos os caminhos possíveis em largura**, começando da raiz (estado inicial), expandindo **nível por nível**, até encontrar:

- O estado objetivo (`goal`)
    
- Ou **todos os caminhos mínimos** até um certo nível
    

---

## 🌊 Como ela "pensa":

Imagine um rio que se expande para todos os lados ao mesmo tempo. Ele visita todos os vizinhos do primeiro nível antes de prosseguir para os próximos níveis.

---

## 📦 Estruturas de Dados

|Estrutura|Finalidade|
|---|---|
|**Fila (queue)**|Armazena os nós que serão expandidos em ordem FIFO|
|**Visitados (set/list)**|Garante que nenhum estado será expandido duas vezes|
|**Pais / Caminho**|Guarda de onde cada estado veio, para reconstruir o caminho|

---

## 🔁 Passo a Passo do Algoritmo

```python
from collections import deque

def bfs(start, goal, get_neighbors):
    fila = deque()
    fila.append([start])  # cada item é um caminho, não só um nó!
    visitados = set()
    visitados.add(start)

    while fila:
        caminho = fila.popleft()
        no_atual = caminho[-1]

        if no_atual == goal:
            return caminho  # Caminho encontrado!

        for vizinho in get_neighbors(no_atual):
            if vizinho not in visitados:
                visitados.add(vizinho)
                novo_caminho = caminho + [vizinho]
                fila.append(novo_caminho)

    return None  # Se não encontrar
```

---

## ✅ Propriedades da BFS

|Propriedade|Valor|
|---|---|
|**Completa**|✔️ Sim (se o grafo for finito)|
|**Ótima**|✔️ Sim (se custo uniforme entre arestas)|
|**Tempo**|O(bd)O(b^d)|
|**Espaço**|O(bd)O(b^d)|
|**Tipo de Busca**|Cega (não usa heurística)|

- `b`: fator de ramificação (número médio de vizinhos por nó)
    
- `d`: profundidade da solução mais rasa
    

---

## 🧠 Comparação com outras buscas

| Algoritmo | Ordem de expansão  | Ótima? | Precisa de Heurística? |
| --------- | ------------------ | ------ | ---------------------- |
| BFS       | Nível por nível    | ✔️     | ❌                      |
| [[DFS]]   | Profundidade total | ❌      | ❌                      |
| UCS       | Menor custo total  | ✔️     | ❌                      |
| A*        | Custo + heurística | ✔️     | ✔️                     |

---

## 📊 Simulação Gráfica da Expansão (Grade 3x3):

```
(1,1) - (1,2) - (1,3)
  |       |       |
(2,1) - (2,2) - (2,3)
  |       |       |
(3,1) - (3,2) - (3,3)
```

### Caminho BFS de (1,1) até (3,3):

Ordem de visita:

```
[(1,1)], [(1,2), (2,1)], [(1,3), (2,2), (3,1)], ...
```

Ele **não pega o mais direto**. Ele explora todos os caminhos de mesmo comprimento primeiro.

---

## 📎 Aplicações Reais da BFS

|Aplicação|Uso|
|---|---|
|Resolução de labirintos|Encontrar caminhos curtos|
|Web Crawlers|Explorar links por nível|
|Problemas de jogos tabuleiro|Encontrar menor sequência de jogadas|
|Redes sociais|Encontrar amigos em comum, graus de separação|

---

## 🎮 Mini-Desafio (nível 1):

> Considere o grid abaixo. As células com “X” são bloqueadas:

```
S . .
X X .
. . G
```

- S = Start = (0,0)
    
- G = Goal = (2,2)
    

1. Simule **manualmente** a BFS
    
2. Liste a ordem de visita dos nós
    
3. Qual é o caminho encontrado?
    

Posso corrigir seu resultado depois se quiser 🧠

---

## 🔍 Deseja agora:

1. Resolver esse mini-desafio?
    
2. Ver como BFS se adapta para grafos com ciclos?
    
3. Aprender a **visualizar BFS passo a passo** com grafo?
    
4. Comparar com DFS na prática?
    

Você comanda a jornada!