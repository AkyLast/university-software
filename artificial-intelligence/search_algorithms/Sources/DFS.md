# 🧠 BUSCA EM PROFUNDIDADE (DFS) — Aprofundamento Total

---

## 📘 PARTE 1 — Intuição e Metáfora

Imagine explorar uma caverna: você escolhe um túnel e vai até onde der. Só quando não há mais saída, você volta e tenta outro caminho. Essa é a essência da **Busca em Profundidade**.

---

## 🎯 Objetivo da DFS

A **DFS** tenta encontrar um objetivo explorando o caminho o **mais profundamente possível**, antes de retroceder e tentar caminhos alternativos.

---

## 🧱 Estrutura de Dados

|Estrutura|Função|
|---|---|
|**Pilha (stack)**|Armazena o caminho atual de forma LIFO (último a entrar, primeiro a sair)|
|**Visitados**|Evita revisitar nós (importante em grafos com ciclos)|
|**Pai / caminho**|Reconstrói o caminho percorrido (opcional)|

---

## 🔁 Pseudocódigo Recursivo

```python
def dfs(grafo, atual, visitado=set()):
    visitado.add(atual)
    for vizinho in grafo[atual]:
        if vizinho not in visitado:
            dfs(grafo, vizinho, visitado)
```

---

## 🔁 Pseudocódigo com Pilha (versão iterativa)

```python
def dfs_iterativa(grafo, inicio):
    pilha = [inicio]
    visitado = set()

    while pilha:
        atual = pilha.pop()
        if atual not in visitado:
            visitado.add(atual)
            for vizinho in reversed(grafo[atual]):
                pilha.append(vizinho)
```

> A ordem dos vizinhos importa! Inverter garante que os primeiros vizinhos sejam explorados primeiro.

---

## 🔍 Propriedades

|Propriedade|Valor|
|---|---|
|**Completa**|❌ Não (pode se perder em ciclos infinitos)|
|**Ótima**|❌ Não (não garante menor caminho)|
|**Tempo**|O(V+E)O(V + E)|
|**Espaço**|O(d)O(d) (recursão) ou O(V)O(V) (iterativa)|

---

## 🌐 Comparação com BFS

|Critério|BFS|DFS|
|---|---|---|
|Estratégia|Amplitude (nível por nível)|Profundidade (vai até o fim)|
|Estrutura|Fila (FIFO)|Pilha (LIFO ou recursão)|
|Ótima|✔️ (se custo uniforme)|❌|
|Completa|✔️ (em grafos finitos)|❌ (se ciclos não forem tratados)|
|Memória|Alta: O(bd)O(b^d)|Baixa: O(d)O(d)|
|Útil em|Menor caminho|Exploração total, puzzles, backtracking|

---

## 🧠 Exemplo com grafo simples

```
      A
     / \
    B   C
   /|   |\
  D E   F G
```

### DFS:

1. A
    
2. B
    
3. D
    
4. E
    
5. C
    
6. F
    
7. G
    

---

## 📦 DFS com Caminho

Se quiser **encontrar um caminho** até um objetivo com DFS:

```python
def dfs_caminho(grafo, atual, objetivo, caminho=[], visitado=set()):
    caminho = caminho + [atual]
    visitado.add(atual)

    if atual == objetivo:
        return caminho

    for vizinho in grafo[atual]:
        if vizinho not in visitado:
            resultado = dfs_caminho(grafo, vizinho, objetivo, caminho, visitado)
            if resultado:
                return resultado
    return None
```

---

## 🧬 Aplicações Reais

|Área|Uso|
|---|---|
|🔬 Bioinformática|Caminhos entre genes/regiões|
|🧠 IA com backtracking|Jogos como Sudoku, N-Queens|
|🧪 Teoria dos Grafos|Detectar ciclos, pontes e componentes conexas|
|🌐 Internet/Redes|Verificar conectividade entre servidores|
|🧗 Otimização|Exploração total de estados em busca de solução|
|💾 Análise de dependência|Compiladores, sistemas de build (DFS com ordenação topológica)|

---

## 🧠 DFS em Árvores Binárias (DFS = pré-ordem)

DFS é a base das **três ordens de percursos**:

1. **Pré-ordem** (visita o nó antes dos filhos)
    
2. **In-ordem** (esquerda → raiz → direita)
    
3. **Pós-ordem** (visita filhos antes do nó)
    

---

## 🎮 Mini-Desafio DFS

> Você tem esse labirinto (grafo implícito):

```
S . .
. X .
. . G
```

- S = (0,0)
    
- G = (2,2)
    
- X = (1,1) = obstáculo
    

**Tente simular a DFS manualmente**, encontrando o primeiro caminho até o objetivo.  
Depois posso corrigir e comparar com o da BFS!

---

## 📚 Resumo

|Recurso|BFS|DFS|
|---|---|---|
|Forma de busca|Largura|Profundidade|
|Memória|Alta|Baixa|
|Ótima|Sim (uniforme)|Não|
|Completa|Sim (em grafos finitos)|Não (ciclos sem controle)|
|Usos principais|Caminhos mínimos|Exploração total, backtracking|

---

## 🔚 Próximos Passos:

1. Resolver o mini-desafio do labirinto via DFS?
    
2. Estudar **detecção de ciclos com DFS**?
    
3. Entender **ordenação topológica** com DFS?
    
4. Avançar para o **UCS (Uniform Cost Search)**?
    
---

Vamos aprofundar a **Busca em Profundidade (DFS)** com **código comentado, variantes e aplicações concretas**, tanto **recursiva quanto iterativa**, incluindo:

- Reconstrução de caminhos
    
- Detecção de ciclos
    
- DFS para ordenação topológica
    
- DFS com pesos e limitação de profundidade
    
- Representação visual da pilha de chamadas
    

---

## 📘 1. DFS Recursiva — Base com caminho e reconstrução

### 🧠 Objetivo: encontrar o **primeiro caminho possível** entre dois nós

```python
def dfs_caminho(grafo, atual, objetivo, caminho=None, visitado=None):
    if caminho is None:
        caminho = []
    if visitado is None:
        visitado = set()

    caminho.append(atual)
    visitado.add(atual)

    if atual == objetivo:
        return caminho  # Retorna caminho completo

    for vizinho in grafo[atual]:
        if vizinho not in visitado:
            resultado = dfs_caminho(grafo, vizinho, objetivo, caminho.copy(), visitado.copy())
            if resultado:
                return resultado

    return None  # Não encontrou
```

### 🔎 Exemplo de uso

```python
grafo = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': [],
    'F': []
}

print(dfs_caminho(grafo, 'A', 'E'))
# Exemplo de saída: ['A', 'B', 'E']
```

---

## 📘 2. DFS Iterativa — Com Pilha explícita

### 🧠 Útil em ambientes sem suporte a recursão profunda

```python
def dfs_iterativa(grafo, inicio, objetivo):
    pilha = [(inicio, [inicio])]
    visitado = set()

    while pilha:
        atual, caminho = pilha.pop()

        if atual in visitado:
            continue
        visitado.add(atual)

        if atual == objetivo:
            return caminho

        for vizinho in reversed(grafo[atual]):
            if vizinho not in visitado:
                pilha.append((vizinho, caminho + [vizinho]))

    return None
```

---

## 📘 3. DFS para Detecção de Ciclos (em grafos direcionados)

```python
def dfs_tem_ciclo(grafo):
    visitado = set()
    em_recursao = set()

    def visitar(n):
        if n in em_recursao:
            return True  # Detecção de ciclo

        if n in visitado:
            return False

        visitado.add(n)
        em_recursao.add(n)

        for vizinho in grafo.get(n, []):
            if visitar(vizinho):
                return True

        em_recursao.remove(n)
        return False

    for no in grafo:
        if visitar(no):
            return True

    return False
```

---

## 📘 4. DFS com Ordenação Topológica

> Útil em sistemas de **dependência** (ex: compiladores)

```python
def ordenacao_topologica(grafo):
    visitado = set()
    pilha = []

    def dfs(no):
        if no in visitado:
            return
        visitado.add(no)

        for vizinho in grafo[no]:
            dfs(vizinho)

        pilha.append(no)  # pós-ordem

    for no in grafo:
        if no not in visitado:
            dfs(no)

    return pilha[::-1]  # inverso da pós-ordem
```

---

## 📘 5. DFS com Profundidade Máxima (ex: Iterative Deepening)

> Útil em problemas onde a profundidade é limitada (como puzzles)

```python
def dfs_limitada(grafo, atual, objetivo, limite, caminho=None):
    if caminho is None:
        caminho = []

    caminho.append(atual)

    if atual == objetivo:
        return caminho

    if limite == 0:
        return None

    for vizinho in grafo[atual]:
        if vizinho not in caminho:
            resultado = dfs_limitada(grafo, vizinho, objetivo, limite - 1, caminho.copy())
            if resultado:
                return resultado

    return None
```

---

## 📘 6. Visualização da Pilha (profundidade)

Vamos simular um print da **pilha de chamadas recursivas**:

```python
def dfs_debug(grafo, atual, objetivo, caminho=None, profundidade=0):
    if caminho is None:
        caminho = []

    caminho.append(atual)
    print("  " * profundidade + f"> Entrando em: {atual}")

    if atual == objetivo:
        print("  " * profundidade + f"✔️ Objetivo encontrado: {caminho}")
        return caminho

    for vizinho in grafo[atual]:
        if vizinho not in caminho:
            resultado = dfs_debug(grafo, vizinho, objetivo, caminho.copy(), profundidade + 1)
            if resultado:
                return resultado

    print("  " * profundidade + f"↩️ Retornando de: {atual}")
    return None
```

### 📈 Exemplo:

```python
grafo = {
    'S': ['A', 'B'],
    'A': ['C'],
    'B': ['D'],
    'C': ['G'],
    'D': [],
    'G': []
}
dfs_debug(grafo, 'S', 'G')
```

Saída esperada:

```
> Entrando em: S
  > Entrando em: A
    > Entrando em: C
      > Entrando em: G
      ✔️ Objetivo encontrado: ['S', 'A', 'C', 'G']
```

---

## 📘 7. Grafo com obstáculos — Exemplo com coordenadas

Para DFS com labirinto/matriz:

```python
def dfs_labirinto(matriz, atual, objetivo, visitado=None, caminho=None):
    if visitado is None:
        visitado = set()
    if caminho is None:
        caminho = []

    x, y = atual
    if (x, y) in visitado or matriz[x][y] == 'X':
        return None

    visitado.add((x, y))
    caminho = caminho + [atual]

    if atual == objetivo:
        return caminho

    movimentos = [(0,1), (1,0), (0,-1), (-1,0)]  # direita, baixo, esquerda, cima

    for dx, dy in movimentos:
        nx, ny = x + dx, y + dy
        if 0 <= nx < len(matriz) and 0 <= ny < len(matriz[0]):
            resultado = dfs_labirinto(matriz, (nx, ny), objetivo, visitado, caminho)
            if resultado:
                return resultado

    return None
```

Exemplo:

```python
lab = [
    ['S', '.', '.'],
    ['.', 'X', '.'],
    ['.', '.', 'G']
]
dfs_labirinto(lab, (0, 0), (2, 2))
```

---

## 🧠 Resumo Profundo das DFS Variantes

|Variante|Função|
|---|---|
|**Recursiva pura**|Exploração profunda rápida|
|**Iterativa**|Usada em ambientes limitados (sem stack overflow)|
|**Com caminho**|Retorna passo a passo|
|**Com detecção de ciclos**|Importante em grafos direcionados|
|**Ordenação topológica**|Dependência de tarefas|
|**Limite de profundidade**|Base para IDDFS e problemas de corte|
|**Com labirinto**|Problemas espaciais e de navegação|

---

## 🧪 Desafios sugeridos

1. Adapte a DFS para encontrar **todos os caminhos possíveis** entre dois nós.
    
2. Use DFS para verificar se um grafo é **fortemente conexo**.
    
3. Implemente **DFS bidirecional** (experimentalmente).
    

---

Quer que aprofundemos um desses pontos específicos com prova teórica, visualização gráfica, ou deseja seguir para **UCS (Busca de Custo Uniforme)** ou *_DFS Iterativa com limite (base para IDDFS e A_)**?Vamos aprofundar a **Busca em Profundidade (DFS)** com **código comentado, variantes e aplicações concretas**, tanto **recursiva quanto iterativa**, incluindo:

* Reconstrução de caminhos
* Detecção de ciclos
* DFS para ordenação topológica
* DFS com pesos e limitação de profundidade
* Representação visual da pilha de chamadas

---

## 📘 1. DFS Recursiva — Base com caminho e reconstrução

### 🧠 Objetivo: encontrar o **primeiro caminho possível** entre dois nós

```python
def dfs_caminho(grafo, atual, objetivo, caminho=None, visitado=None):
    if caminho is None:
        caminho = []
    if visitado is None:
        visitado = set()

    caminho.append(atual)
    visitado.add(atual)

    if atual == objetivo:
        return caminho  # Retorna caminho completo

    for vizinho in grafo[atual]:
        if vizinho not in visitado:
            resultado = dfs_caminho(grafo, vizinho, objetivo, caminho.copy(), visitado.copy())
            if resultado:
                return resultado

    return None  # Não encontrou
```

### 🔎 Exemplo de uso

```python
grafo = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': [],
    'F': []
}

print(dfs_caminho(grafo, 'A', 'E'))
# Exemplo de saída: ['A', 'B', 'E']
```

---

## 📘 2. DFS Iterativa — Com Pilha explícita

### 🧠 Útil em ambientes sem suporte a recursão profunda

```python
def dfs_iterativa(grafo, inicio, objetivo):
    pilha = [(inicio, [inicio])]
    visitado = set()

    while pilha:
        atual, caminho = pilha.pop()

        if atual in visitado:
            continue
        visitado.add(atual)

        if atual == objetivo:
            return caminho

        for vizinho in reversed(grafo[atual]):
            if vizinho not in visitado:
                pilha.append((vizinho, caminho + [vizinho]))

    return None
```

---

## 📘 3. DFS para Detecção de Ciclos (em grafos direcionados)

```python
def dfs_tem_ciclo(grafo):
    visitado = set()
    em_recursao = set()

    def visitar(n):
        if n in em_recursao:
            return True  # Detecção de ciclo

        if n in visitado:
            return False

        visitado.add(n)
        em_recursao.add(n)

        for vizinho in grafo.get(n, []):
            if visitar(vizinho):
                return True

        em_recursao.remove(n)
        return False

    for no in grafo:
        if visitar(no):
            return True

    return False
```

---

## 📘 4. DFS com Ordenação Topológica

> Útil em sistemas de **dependência** (ex: compiladores)

```python
def ordenacao_topologica(grafo):
    visitado = set()
    pilha = []

    def dfs(no):
        if no in visitado:
            return
        visitado.add(no)

        for vizinho in grafo[no]:
            dfs(vizinho)

        pilha.append(no)  # pós-ordem

    for no in grafo:
        if no not in visitado:
            dfs(no)

    return pilha[::-1]  # inverso da pós-ordem
```

---

## 📘 5. DFS com Profundidade Máxima (ex: Iterative Deepening)

> Útil em problemas onde a profundidade é limitada (como puzzles)

```python
def dfs_limitada(grafo, atual, objetivo, limite, caminho=None):
    if caminho is None:
        caminho = []

    caminho.append(atual)

    if atual == objetivo:
        return caminho

    if limite == 0:
        return None

    for vizinho in grafo[atual]:
        if vizinho not in caminho:
            resultado = dfs_limitada(grafo, vizinho, objetivo, limite - 1, caminho.copy())
            if resultado:
                return resultado

    return None
```

---

## 📘 6. Visualização da Pilha (profundidade)

Vamos simular um print da **pilha de chamadas recursivas**:

```python
def dfs_debug(grafo, atual, objetivo, caminho=None, profundidade=0):
    if caminho is None:
        caminho = []

    caminho.append(atual)
    print("  " * profundidade + f"> Entrando em: {atual}")

    if atual == objetivo:
        print("  " * profundidade + f"✔️ Objetivo encontrado: {caminho}")
        return caminho

    for vizinho in grafo[atual]:
        if vizinho not in caminho:
            resultado = dfs_debug(grafo, vizinho, objetivo, caminho.copy(), profundidade + 1)
            if resultado:
                return resultado

    print("  " * profundidade + f"↩️ Retornando de: {atual}")
    return None
```

### 📈 Exemplo:

```python
grafo = {
    'S': ['A', 'B'],
    'A': ['C'],
    'B': ['D'],
    'C': ['G'],
    'D': [],
    'G': []
}
dfs_debug(grafo, 'S', 'G')
```

Saída esperada:

```
> Entrando em: S
  > Entrando em: A
    > Entrando em: C
      > Entrando em: G
      ✔️ Objetivo encontrado: ['S', 'A', 'C', 'G']
```

---

## 📘 7. Grafo com obstáculos — Exemplo com coordenadas

Para DFS com labirinto/matriz:

```python
def dfs_labirinto(matriz, atual, objetivo, visitado=None, caminho=None):
    if visitado is None:
        visitado = set()
    if caminho is None:
        caminho = []

    x, y = atual
    if (x, y) in visitado or matriz[x][y] == 'X':
        return None

    visitado.add((x, y))
    caminho = caminho + [atual]

    if atual == objetivo:
        return caminho

    movimentos = [(0,1), (1,0), (0,-1), (-1,0)]  # direita, baixo, esquerda, cima

    for dx, dy in movimentos:
        nx, ny = x + dx, y + dy
        if 0 <= nx < len(matriz) and 0 <= ny < len(matriz[0]):
            resultado = dfs_labirinto(matriz, (nx, ny), objetivo, visitado, caminho)
            if resultado:
                return resultado

    return None
```

Exemplo:

```python
lab = [
    ['S', '.', '.'],
    ['.', 'X', '.'],
    ['.', '.', 'G']
]
dfs_labirinto(lab, (0, 0), (2, 2))
```

---

## 🧠 Resumo Profundo das DFS Variantes

| Variante                   | Função                                            |
| -------------------------- | ------------------------------------------------- |
| **Recursiva pura**         | Exploração profunda rápida                        |
| **Iterativa**              | Usada em ambientes limitados (sem stack overflow) |
| **Com caminho**            | Retorna passo a passo                             |
| **Com detecção de ciclos** | Importante em grafos direcionados                 |
| **Ordenação topológica**   | Dependência de tarefas                            |
| **Limite de profundidade** | Base para IDDFS e problemas de corte              |
| **Com labirinto**          | Problemas espaciais e de navegação                |

---

## 🧪 Desafios sugeridos

1. Adapte a DFS para encontrar **todos os caminhos possíveis** entre dois nós.
2. Use DFS para verificar se um grafo é **fortemente conexo**.
3. Implemente **DFS bidirecional** (experimentalmente).

---

Quer que aprofundemos um desses pontos específicos com prova teórica, visualização gráfica, ou deseja seguir para **UCS (Busca de Custo Uniforme)** ou \**DFS Iterativa com limite (base para IDDFS e A*)\*\*?
Vamos aprofundar a **Busca em Profundidade (DFS)** com **código comentado, variantes e aplicações concretas**, tanto **recursiva quanto iterativa**, incluindo:

* Reconstrução de caminhos
* Detecção de ciclos
* DFS para ordenação topológica
* DFS com pesos e limitação de profundidade
* Representação visual da pilha de chamadas

---

## 📘 1. DFS Recursiva — Base com caminho e reconstrução

### 🧠 Objetivo: encontrar o **primeiro caminho possível** entre dois nós

```python
def dfs_caminho(grafo, atual, objetivo, caminho=None, visitado=None):
    if caminho is None:
        caminho = []
    if visitado is None:
        visitado = set()

    caminho.append(atual)
    visitado.add(atual)

    if atual == objetivo:
        return caminho  # Retorna caminho completo

    for vizinho in grafo[atual]:
        if vizinho not in visitado:
            resultado = dfs_caminho(grafo, vizinho, objetivo, caminho.copy(), visitado.copy())
            if resultado:
                return resultado

    return None  # Não encontrou
```

### 🔎 Exemplo de uso

```python
grafo = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': [],
    'F': []
}

print(dfs_caminho(grafo, 'A', 'E'))
# Exemplo de saída: ['A', 'B', 'E']
```

---

## 📘 2. DFS Iterativa — Com Pilha explícita

### 🧠 Útil em ambientes sem suporte a recursão profunda

```python
def dfs_iterativa(grafo, inicio, objetivo):
    pilha = [(inicio, [inicio])]
    visitado = set()

    while pilha:
        atual, caminho = pilha.pop()

        if atual in visitado:
            continue
        visitado.add(atual)

        if atual == objetivo:
            return caminho

        for vizinho in reversed(grafo[atual]):
            if vizinho not in visitado:
                pilha.append((vizinho, caminho + [vizinho]))

    return None
```

---

## 📘 3. DFS para Detecção de Ciclos (em grafos direcionados)

```python
def dfs_tem_ciclo(grafo):
    visitado = set()
    em_recursao = set()

    def visitar(n):
        if n in em_recursao:
            return True  # Detecção de ciclo

        if n in visitado:
            return False

        visitado.add(n)
        em_recursao.add(n)

        for vizinho in grafo.get(n, []):
            if visitar(vizinho):
                return True

        em_recursao.remove(n)
        return False

    for no in grafo:
        if visitar(no):
            return True

    return False
```

---

## 📘 4. DFS com Ordenação Topológica

> Útil em sistemas de **dependência** (ex: compiladores)

```python
def ordenacao_topologica(grafo):
    visitado = set()
    pilha = []

    def dfs(no):
        if no in visitado:
            return
        visitado.add(no)

        for vizinho in grafo[no]:
            dfs(vizinho)

        pilha.append(no)  # pós-ordem

    for no in grafo:
        if no not in visitado:
            dfs(no)

    return pilha[::-1]  # inverso da pós-ordem
```

---

## 📘 5. DFS com Profundidade Máxima (ex: Iterative Deepening)

> Útil em problemas onde a profundidade é limitada (como puzzles)

```python
def dfs_limitada(grafo, atual, objetivo, limite, caminho=None):
    if caminho is None:
        caminho = []

    caminho.append(atual)

    if atual == objetivo:
        return caminho

    if limite == 0:
        return None

    for vizinho in grafo[atual]:
        if vizinho not in caminho:
            resultado = dfs_limitada(grafo, vizinho, objetivo, limite - 1, caminho.copy())
            if resultado:
                return resultado

    return None
```

---

## 📘 6. Visualização da Pilha (profundidade)

Vamos simular um print da **pilha de chamadas recursivas**:

```python
def dfs_debug(grafo, atual, objetivo, caminho=None, profundidade=0):
    if caminho is None:
        caminho = []

    caminho.append(atual)
    print("  " * profundidade + f"> Entrando em: {atual}")

    if atual == objetivo:
        print("  " * profundidade + f"✔️ Objetivo encontrado: {caminho}")
        return caminho

    for vizinho in grafo[atual]:
        if vizinho not in caminho:
            resultado = dfs_debug(grafo, vizinho, objetivo, caminho.copy(), profundidade + 1)
            if resultado:
                return resultado

    print("  " * profundidade + f"↩️ Retornando de: {atual}")
    return None
```

### 📈 Exemplo:

```python
grafo = {
    'S': ['A', 'B'],
    'A': ['C'],
    'B': ['D'],
    'C': ['G'],
    'D': [],
    'G': []
}
dfs_debug(grafo, 'S', 'G')
```

Saída esperada:

```
> Entrando em: S
  > Entrando em: A
    > Entrando em: C
      > Entrando em: G
      ✔️ Objetivo encontrado: ['S', 'A', 'C', 'G']
```

---

## 📘 7. Grafo com obstáculos — Exemplo com coordenadas

Para DFS com labirinto/matriz:

```python
def dfs_labirinto(matriz, atual, objetivo, visitado=None, caminho=None):
    if visitado is None:
        visitado = set()
    if caminho is None:
        caminho = []

    x, y = atual
    if (x, y) in visitado or matriz[x][y] == 'X':
        return None

    visitado.add((x, y))
    caminho = caminho + [atual]

    if atual == objetivo:
        return caminho

    movimentos = [(0,1), (1,0), (0,-1), (-1,0)]  # direita, baixo, esquerda, cima

    for dx, dy in movimentos:
        nx, ny = x + dx, y + dy
        if 0 <= nx < len(matriz) and 0 <= ny < len(matriz[0]):
            resultado = dfs_labirinto(matriz, (nx, ny), objetivo, visitado, caminho)
            if resultado:
                return resultado

    return None
```

Exemplo:

```python
lab = [
    ['S', '.', '.'],
    ['.', 'X', '.'],
    ['.', '.', 'G']
]
dfs_labirinto(lab, (0, 0), (2, 2))
```

---

## 🧠 Resumo Profundo das DFS Variantes

| Variante                   | Função                                            |
| -------------------------- | ------------------------------------------------- |
| **Recursiva pura**         | Exploração profunda rápida                        |
| **Iterativa**              | Usada em ambientes limitados (sem stack overflow) |
| **Com caminho**            | Retorna passo a passo                             |
| **Com detecção de ciclos** | Importante em grafos direcionados                 |
| **Ordenação topológica**   | Dependência de tarefas                            |
| **Limite de profundidade** | Base para IDDFS e problemas de corte              |
| **Com labirinto**          | Problemas espaciais e de navegação                |

---

## 🧪 Desafios sugeridos

1. Adapte a DFS para encontrar **todos os caminhos possíveis** entre dois nós.
2. Use DFS para verificar se um grafo é **fortemente conexo**.
3. Implemente **DFS bidirecional** (experimentalmente).

---
