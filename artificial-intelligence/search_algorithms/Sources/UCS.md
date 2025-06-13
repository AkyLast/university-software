# 🧠 UCS – Uniform Cost Search (Busca de Custo Uniforme)

---

## 🧭 1. Intuição

A UCS é como um GPS que **sempre escolhe o caminho mais barato acumulado até agora**. Ela expande os nós **pelo menor custo total desde a origem**, e não pela profundidade ou pela ordem de chegada.

> Imagine procurar o caminho mais barato entre cidades, considerando o custo real (ex: km ou pedágios), não apenas o número de estradas.

---

## 🧱 2. Estruturas utilizadas

|Estrutura|Função|
|---|---|
|**Fila de Prioridade**|Organiza os nós por custo acumulado g(n)g(n)|
|**Visitados**|Evita reexplorar estados com menor custo|
|**Mapa de custos**|Guarda o menor custo conhecido para cada nó|

---

## 🔁 3. Pseudocódigo

```python
import heapq

def ucs(grafo, inicio, objetivo):
    fila = [(0, inicio, [])]  # (custo_acumulado, nó_atual, caminho)
    visitado = {}

    while fila:
        custo, atual, caminho = heapq.heappop(fila)

        if atual in visitado and visitado[atual] <= custo:
            continue

        visitado[atual] = custo
        caminho = caminho + [atual]

        if atual == objetivo:
            return caminho, custo

        for vizinho, custo_vizinho in grafo[atual]:
            heapq.heappush(fila, (custo + custo_vizinho, vizinho, caminho))

    return None, float('inf')  # sem solução
```

---

## 🎓 4. Propriedades Teóricas

|Propriedade|UCS|
|---|---|
|**Completa**|✅ Sim (se custos ≥ 0)|
|**Ótima**|✅ Sim (garante menor custo)|
|**Tempo**|O(b1+⌊C∗/ϵ⌋)O(b^{1+\lfloor C^*/\epsilon \rfloor}) (ver abaixo)|
|**Espaço**|Mesmo que o tempo (devido à fila)|

> Onde:
> 
> - C∗C^* é o custo da solução ótima
>     
> - ϵ\epsilon é o menor custo positivo de aresta
>     

---

## 📈 5. Comparação com DFS, BFS

|Algoritmo|Critério de Expansão|Ótimo?|Usa custo?|Estrutura|
|---|---|---|---|---|
|DFS|Profundidade|❌|❌|Pilha|
|BFS|Distância (número de passos)|✅|❌|Fila|
|UCS|Menor custo acumulado|✅|✅|Fila de prioridade|

---

## 🌍 6. Exemplo visual: mapa com pesos

Grafo com custos:

```
    A
  /   \
1       4
B       C
 \     /
  2   1
    D
     \
      3
       G
```

Representado como:

```python
grafo = {
    'A': [('B', 1), ('C', 4)],
    'B': [('D', 2)],
    'C': [('D', 1)],
    'D': [('G', 3)],
    'G': []
}
```

Execução:

- A → B → D → G: custo 1 + 2 + 3 = **6** ✅
    
- A → C → D → G: custo 4 + 1 + 3 = **8** ❌
    

A UCS encontrará o caminho A → B → D → G.

---

## 🔍 7. UCS ≠ Dijkstra?

✅ **Sim, UCS e Dijkstra são essencialmente o mesmo algoritmo** — a diferença é de contexto:

|Termo|Usado em|
|---|---|
|UCS|Inteligência Artificial|
|Dijkstra|Ciência da Computação/Redes|

Ambos usam **fila de prioridade** e expandem o caminho de **menor custo acumulado**.

---

## 🧪 8. Aplicações do mundo real

|Área|Uso|
|---|---|
|GPS e Mapas|Menor distância real entre locais|
|Robótica|Caminho mais curto com consumo energético mínimo|
|Planejamento IA|Planos com menor custo de ações|
|Redes de computadores|Roteamento ótimo de pacotes (Ex: OSPF)|
|Jogos de tabuleiro|Busca com custo (ex: tempo ou penalidades)|

---

## ⚠️ 9. Cuidados

- Se houver **ciclo com custo 0**, pode entrar em laço infinito. ✅ Use controle de visitados com o menor custo.
    
- Funciona **somente com custos não-negativos** (como o Dijkstra).
    

---

## 🧠 10. Mini-desafio UCS

**Grafo com pesos**:

```python
grafo = {
    'S': [('A', 2), ('B', 5)],
    'A': [('C', 2), ('D', 4)],
    'B': [('D', 1)],
    'C': [('G', 3)],
    'D': [('G', 2)],
    'G': []
}
```

🧩 Pergunta:

- Qual o caminho mais barato de S até G?
    
- Qual o custo total?
    

> Podemos resolver juntos ou você tenta primeiro e te dou o feedback!

---

## ✅ Próximos passos sugeridos:

1. Resolver o **mini-desafio UCS**
    
2. Aprender **IDDFS (Busca em profundidade iterativa com limite)**
    
3. Começar **A*** (heurística + UCS)
    
4. Implementar UCS com **grafo de mapa real** (usando coordenadas)
    
5. Criar **visualizador passo-a-passo da UCS**
    
---

# 🧠 UCS – Uniform Cost Search (Busca de Custo Uniforme)

---

## 🧭 1. Intuição

A UCS é como um GPS que **sempre escolhe o caminho mais barato acumulado até agora**. Ela expande os nós **pelo menor custo total desde a origem**, e não pela profundidade ou pela ordem de chegada.

> Imagine procurar o caminho mais barato entre cidades, considerando o custo real (ex: km ou pedágios), não apenas o número de estradas.

---

## 🧱 2. Estruturas utilizadas

|Estrutura|Função|
|---|---|
|**Fila de Prioridade**|Organiza os nós por custo acumulado g(n)g(n)|
|**Visitados**|Evita reexplorar estados com menor custo|
|**Mapa de custos**|Guarda o menor custo conhecido para cada nó|

---

## 🔁 3. Pseudocódigo

```python
import heapq

def ucs(grafo, inicio, objetivo):
    fila = [(0, inicio, [])]  # (custo_acumulado, nó_atual, caminho)
    visitado = {}

    while fila:
        custo, atual, caminho = heapq.heappop(fila)

        if atual in visitado and visitado[atual] <= custo:
            continue

        visitado[atual] = custo
        caminho = caminho + [atual]

        if atual == objetivo:
            return caminho, custo

        for vizinho, custo_vizinho in grafo[atual]:
            heapq.heappush(fila, (custo + custo_vizinho, vizinho, caminho))

    return None, float('inf')  # sem solução
```

---

## 🎓 4. Propriedades Teóricas

|Propriedade|UCS|
|---|---|
|**Completa**|✅ Sim (se custos ≥ 0)|
|**Ótima**|✅ Sim (garante menor custo)|
|**Tempo**|O(b1+⌊C∗/ϵ⌋)O(b^{1+\lfloor C^*/\epsilon \rfloor}) (ver abaixo)|
|**Espaço**|Mesmo que o tempo (devido à fila)|

> Onde:
> 
> - C∗C^* é o custo da solução ótima
>     
> - ϵ\epsilon é o menor custo positivo de aresta
>     

---

## 📈 5. Comparação com DFS, BFS

|Algoritmo|Critério de Expansão|Ótimo?|Usa custo?|Estrutura|
|---|---|---|---|---|
|DFS|Profundidade|❌|❌|Pilha|
|BFS|Distância (número de passos)|✅|❌|Fila|
|UCS|Menor custo acumulado|✅|✅|Fila de prioridade|

---

## 🌍 6. Exemplo visual: mapa com pesos

Grafo com custos:

```
    A
  /   \
1       4
B       C
 \     /
  2   1
    D
     \
      3
       G
```

Representado como:

```python
grafo = {
    'A': [('B', 1), ('C', 4)],
    'B': [('D', 2)],
    'C': [('D', 1)],
    'D': [('G', 3)],
    'G': []
}
```

Execução:

- A → B → D → G: custo 1 + 2 + 3 = **6** ✅
    
- A → C → D → G: custo 4 + 1 + 3 = **8** ❌
    

A UCS encontrará o caminho A → B → D → G.

---

## 🔍 7. UCS ≠ Dijkstra?

✅ **Sim, UCS e Dijkstra são essencialmente o mesmo algoritmo** — a diferença é de contexto:

|Termo|Usado em|
|---|---|
|UCS|Inteligência Artificial|
|Dijkstra|Ciência da Computação/Redes|

Ambos usam **fila de prioridade** e expandem o caminho de **menor custo acumulado**.

---

## 🧪 8. Aplicações do mundo real

|Área|Uso|
|---|---|
|GPS e Mapas|Menor distância real entre locais|
|Robótica|Caminho mais curto com consumo energético mínimo|
|Planejamento IA|Planos com menor custo de ações|
|Redes de computadores|Roteamento ótimo de pacotes (Ex: OSPF)|
|Jogos de tabuleiro|Busca com custo (ex: tempo ou penalidades)|

---

## ⚠️ 9. Cuidados

- Se houver **ciclo com custo 0**, pode entrar em laço infinito. ✅ Use controle de visitados com o menor custo.
    
- Funciona **somente com custos não-negativos** (como o Dijkstra).
    

---

## 🧠 10. Mini-desafio UCS

**Grafo com pesos**:

```python
grafo = {
    'S': [('A', 2), ('B', 5)],
    'A': [('C', 2), ('D', 4)],
    'B': [('D', 1)],
    'C': [('G', 3)],
    'D': [('G', 2)],
    'G': []
}
```

🧩 Pergunta:

- Qual o caminho mais barato de S até G?
    
- Qual o custo total?
    

> Podemos resolver juntos ou você tenta primeiro e te dou o feedback!

---

## ✅ Próximos passos sugeridos:

1. Resolver o **mini-desafio UCS**
    
2. Aprender **IDDFS (Busca em profundidade iterativa com limite)**
    
3. Começar **A*** (heurística + UCS)
    
4. Implementar UCS com **grafo de mapa real** (usando coordenadas)
    
5. Criar **visualizador passo-a-passo da UCS**
    

Qual caminho você quer seguir agora? Deseja resolver o desafio ou quer seguir direto para UCS + A*?

Perfeito! Vamos nos aprofundar na **implementação prática da UCS (Busca de Custo Uniforme)** com vários recursos adicionais, incluindo:

1. Estrutura base
    
2. Exibição passo a passo da fila
    
3. Reconstrução do caminho
    
4. Controle de nós visitados com custo ótimo
    
5. Visualização em forma de grafo
    
6. Variações com múltiplos objetivos e grafos com ciclos
    

---

## 🔧 1. UCS – Estrutura Base com Comentários Detalhados

```python
import heapq

def ucs(grafo, inicio, objetivo):
    # Fila de prioridade: (custo acumulado, nó atual, caminho até agora)
    fila = [(0, inicio, [])]
    
    # Armazena o menor custo conhecido para cada nó
    visitado = {}

    while fila:
        custo, atual, caminho = heapq.heappop(fila)
        caminho = caminho + [atual]

        # Se esse nó já foi visitado com custo menor, ignore
        if atual in visitado and visitado[atual] <= custo:
            continue
        visitado[atual] = custo

        # Verifica se objetivo foi alcançado
        if atual == objetivo:
            return caminho, custo

        # Explora vizinhos
        for vizinho, custo_vizinho in grafo.get(atual, []):
            heapq.heappush(fila, (custo + custo_vizinho, vizinho, caminho))

    return None, float('inf')
```

---

## 🧪 2. Exemplo Prático com Print Passo-a-Passo

```python
def ucs_verbose(grafo, inicio, objetivo):
    import heapq
    fila = [(0, inicio, [])]
    visitado = {}

    print("🔍 UCS Iniciada")
    
    while fila:
        print(f"📥 Fila: {[ (c,n) for c,n,_ in fila ]}")
        custo, atual, caminho = heapq.heappop(fila)
        caminho = caminho + [atual]
        print(f"➡️ Expandindo: {atual} com custo {custo} | Caminho: {caminho}")

        if atual in visitado and visitado[atual] <= custo:
            print(f"⛔ {atual} já visitado com custo menor. Pulando.")
            continue
        visitado[atual] = custo

        if atual == objetivo:
            print(f"🎯 Objetivo alcançado: {caminho} com custo {custo}")
            return caminho, custo

        for vizinho, custo_vizinho in grafo.get(atual, []):
            novo_custo = custo + custo_vizinho
            print(f"  ➕ Vizinho {vizinho}, novo custo: {novo_custo}")
            heapq.heappush(fila, (novo_custo, vizinho, caminho))

    return None, float('inf')
```

### Exemplo de grafo:

```python
grafo = {
    'S': [('A', 2), ('B', 5)],
    'A': [('C', 2), ('D', 4)],
    'B': [('D', 1)],
    'C': [('G', 3)],
    'D': [('G', 2)],
    'G': []
}

caminho, custo = ucs_verbose(grafo, 'S', 'G')
print(f"\n🧾 Caminho ótimo: {caminho} | Custo total: {custo}")
```

---

## 🧠 3. UCS com múltiplos objetivos

```python
def ucs_multiobjetivo(grafo, inicio, objetivos):
    fila = [(0, inicio, [])]
    visitado = {}

    while fila:
        custo, atual, caminho = heapq.heappop(fila)
        caminho = caminho + [atual]

        if atual in visitado and visitado[atual] <= custo:
            continue
        visitado[atual] = custo

        if atual in objetivos:
            return caminho, custo

        for vizinho, custo_vizinho in grafo.get(atual, []):
            heapq.heappush(fila, (custo + custo_vizinho, vizinho, caminho))

    return None, float('inf')
```

---

## 🔄 4. UCS com grafos cíclicos (teste de robustez)

```python
grafo_ciclico = {
    'A': [('B', 1), ('C', 4)],
    'B': [('A', 1), ('D', 2)],
    'C': [('D', 1)],
    'D': [('A', 3), ('E', 1)],
    'E': []
}
```

Aqui, mesmo com ciclos como A → B → D → A, a UCS encontrará o caminho A → B → D → E com custo ótimo.

---

## 📊 5. Visualização com NetworkX (opcional com gráfico)

```python
import networkx as nx
import matplotlib.pyplot as plt

def desenhar_grafo(grafo):
    G = nx.DiGraph()
    for no, vizinhos in grafo.items():
        for viz, custo in vizinhos:
            G.add_edge(no, viz, weight=custo)
    
    pos = nx.spring_layout(G)
    edge_labels = nx.get_edge_attributes(G, 'weight')

    nx.draw(G, pos, with_labels=True, node_color='lightblue', node_size=2000, font_size=14)
    nx.draw_networkx_edge_labels(G, pos, edge_labels=edge_labels)
    plt.title("📍 Grafo para UCS")
    plt.show()

# Exemplo:
# desenhar_grafo(grafo)
```

---

## 🔁 6. Refatorando com classe (UCS modular)

```python
class UCS:
    def __init__(self, grafo):
        self.grafo = grafo

    def busca(self, inicio, objetivo):
        from heapq import heappush, heappop
        fila = [(0, inicio, [])]
        visitado = {}

        while fila:
            custo, atual, caminho = heappop(fila)
            caminho = caminho + [atual]

            if atual in visitado and visitado[atual] <= custo:
                continue
            visitado[atual] = custo

            if atual == objetivo:
                return caminho, custo

            for vizinho, custo_vizinho in self.grafo.get(atual, []):
                heappush(fila, (custo + custo_vizinho, vizinho, caminho))

        return None, float('inf')
```

---

## 📌 Conclusão

A UCS é:

- **Um Dijkstra disfarçado**, ótimo e seguro se os custos forem positivos.
    
- Ideal para encontrar **caminhos mais baratos**, mesmo que mais longos.
    
- Excelente como **base para A*** e **IDA***.
    

---

## 🧩 Quer praticar agora?

Aqui estão dois desafios:

1. **Modifique a UCS para armazenar não apenas o custo, mas o número de passos.**
    
2. **Adapte a UCS para evitar certos nós (ex: perigosos ou bloqueados).**
    
3. **Implemente UCS para uma grade (labirinto 2D com custos por célula).**
    
