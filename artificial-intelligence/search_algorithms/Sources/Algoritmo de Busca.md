![[Pasted image 20250531213258.png]]



# 🗺️ **Roteiro da Jornada**

### 🔥 **Missão Principal:** Dominar Metodologias de Busca em IA

---

## 📚 **Mapa da Jornada**

|🔢|🌟 Etapa|🎯 Objetivo|
|---|---|---|
|1|**Fundamentos de Busca em IA**|Entender o que é busca, estados e problemas|
|2|**Busca Não Informada**|BFS, DFS, Custo Uniforme, Iterativa|
|3|**Busca Informada (Heurística)**|Greedy, A*, IDA*, funções heurísticas|
|4|**Busca Local e Metaheurísticas**|Hill Climbing, Simulated Annealing, Genéticos|
|5|**Busca em Ambientes Competitivos**|Minimax, Poda Alpha-Beta|
|6|**Otimização e Planejamento Avançado**|Aplicações, Robótica, Planejamento|
|7|**Desafio Final - Projeto de IA**|Resolver um problema real|

---

# 🚀 **Missão 1: Fundamentos de Busca em IA**

## 🎯 Objetivo:

- Entender:  
    ✔️ O que é um problema de busca.  
    ✔️ Como representar estados, ações e soluções.  
    ✔️ Como a IA transforma problemas em busca por soluções.
    

---

## 📜 **Resumo Flashcard**

- **Espaço de Estados:** Conjunto de todos os estados possíveis de um problema.
    
- **Estado Inicial:** Onde tudo começa.
    
- **Estado Meta:** Onde queremos chegar (solução).
    
- **Ações:** O que podemos fazer a partir de cada estado.
    
- **Caminho:** Sequência de ações que leva do inicial ao objetivo.
    
- **Custo:** Quanto custa percorrer um caminho (tempo, distância, energia, etc.).
    

---

## 🎲 **Exemplos Famosos de Busca**

- **Quebra-cabeça 8 peças:** organizar peças na ordem correta.
    
- **Mapa de cidades:** encontrar o caminho mais curto de uma cidade a outra.
    
- **Xadrez:** encontrar a melhor jogada.
    
- **Robô em um labirinto:** sair do ponto A até o ponto B.
    

---

## 💡 **Desafio 1 - "Desenhando o Espaço de Busca"**

**Contexto:**  
Imagine um robô em um labirinto 3x3. Ele começa na célula (1,1) e precisa chegar à célula (3,3).

### 🔧 Tarefa:

1. **Descreva o espaço de estados:**
    
    - Quantos estados existem?
        
    - Qual o estado inicial?
        
    - Qual o estado objetivo?
        
2. **Defina as ações:**
    
    - Quais movimentos o robô pode fazer? (Ex.: cima, baixo, esquerda, direita).
        
3. **Desenhe (ou descreva) um exemplo de caminho possível.**
    
---

# ✅ **Correção e Feedback**

### 🔢 **Questão 1 - Estados:**

- ✔️ Correto!  
    O espaço de estados é composto pelas 9 células da grade 3x3:  
    (1,1),(1,2),(1,3),(2,1),(2,2),(2,3),(3,1),(3,2),(3,3)(1,1), (1,2), (1,3), (2,1), (2,2), (2,3), (3,1), (3,2), (3,3)
    

---

### 🎯 **Questão 2 - Ações:**

- ✔️ **Observação:**  
    Você percebeu algo muito inteligente: **"baixo e direita são suficientes para alcançar (3,3)"**.  
    ✅ Isso é verdade **se e somente se não houver obstáculos** e o objetivo for seguir um caminho direto.
    

Porém, no modelo geral de IA, definimos as ações como:

- **Cima, Baixo, Esquerda, Direita**, pois nem sempre sabemos se o caminho reto é possível (em mapas, labirintos, jogos...).
    

👉 Isso é essencial porque os algoritmos precisam ser gerais, capazes de explorar qualquer caminho válido.

---

### 🏃‍♂️ **Questão 3 - Caminho Exemplo:**

- ✔️ Correto e válido!  
    (1,1)→(1,2)→(2,2)→(2,3)→(3,3)(1,1) → (1,2) → (2,2) → (2,3) → (3,3)  
    ✅ Caminho totalmente viável.
    

---

# 🧠 **Resumo da Missão 1 (Anotar!)**

> ✔️ Um problema de busca em IA é definido por:  
> (EstadoInicial,Ac\co~es,EstadoMeta,Espac\coDeEstados,Custo)(EstadoInicial, Ações, EstadoMeta, EspaçoDeEstados, Custo)

- A IA resolve problemas simulando transições entre estados até encontrar o estado meta.
    

---

# 🚀 **Missão 2: Busca Não Informada**

## 🎯 Objetivo:

Aprender os algoritmos que exploram o espaço de busca **sem informação extra** além da própria estrutura.

---

## 🔍 **Tipos de Busca Não Informada:**

|🔢|Algoritmo|Característica Principal|
|---|---|---|
|1|**Busca em Largura (BFS)**|Explora todos os nós no mesmo nível antes de descer. Garante solução ótima se o custo é igual.|
|2|**Busca em Profundidade (DFS)**|Vai até o fundo antes de voltar. Usa menos memória, mas não garante solução ótima.|
|3|**Busca de Custo Uniforme (UCS)**|Sempre expande o nó com menor custo acumulado. Garante solução ótima com custos variáveis.|
|4|**Busca em Profundidade Iterativa (IDDFS)**|Combina vantagens de BFS e DFS. Profundidade limitada, depois aumenta iterativamente.|

---

## 🧠 **Vamos começar pela Busca em Largura (BFS)**

### 📜 **Definição:**

- Explora primeiro todos os nós no nível mais raso (mais próximo do estado inicial), depois avança para níveis mais profundos.
    

### 🏗️ **Estrutura:**

- Usa uma **fila (FIFO)** para armazenar nós.
    

### ✅ **Propriedades:**

- 🔍 **Completude:** ✔️ (sempre encontra uma solução, se existir)
    
- ⭐ **Ótima:** ✔️ (se todos os custos são iguais)
    
- 🧠 **Complexidade de Tempo:** O(bd)O(b^d)
    
- 🧠 **Complexidade de Espaço:** O(bd)O(b^d)  
    Onde:
    
- bb = fator de ramificação (número médio de ações possíveis por estado)
    
- dd = profundidade da solução mais rasa
    

---

## 👾 **Desafio 2 - BFS na Prática (Teórico e Algoritmo)**

### ✍️ **Parte 1 - Manual:**

Usando o labirinto 3x3:

1. Simule manualmente a execução da **BFS** saindo de (1,1) até (3,3).
    
2. Liste a ordem em que os estados são visitados.
    

---

### 💻 **Parte 2 - Algoritmo (Pseudo ou Código):**

- Escreva o **algoritmo da BFS** em pseudo-código, Python, ou na linguagem que preferir.  
    (Se quiser, posso te fornecer o modelo inicial e você completa!)
    

---

# 🔍 **Parte 1 – Simulação Manual da BFS no Labirinto 3x3**

### ✔️ Estado Inicial: (1,1)

### ✔️ Estado Objetivo: (3,3)

### ✔️ Ações permitidas: **Cima, Baixo, Esquerda, Direita** (movimentos válidos dentro da grade 3x3).

---

## 🚦 **Execução Passo a Passo da BFS:**

### 🧠 **Regras da BFS:**

- Sempre expande o nó mais antigo da fila (Fila = FIFO).
    
- Visita todos os vizinhos antes de descer para os níveis mais profundos.
    

---

### 🔢 **Passo 0 — Estado Inicial:**

Fila: (1,1)(1,1)  
Visitados:

---

### 🔢 **Passo 1 — Expande (1,1):**

Vizinhos válidos: (1,2), (2,1)  
Fila: (1,2),(2,1)(1,2), (2,1)  
Visitados: (1,1)(1,1)

---

### 🔢 **Passo 2 — Expande (1,2):**

Vizinhos válidos: (1,3), (2,2)  
Fila: (2,1),(1,3),(2,2)(2,1), (1,3), (2,2)  
Visitados: (1,1),(1,2)(1,1), (1,2)

---

### 🔢 **Passo 3 — Expande (2,1):**

Vizinhos válidos: (3,1), (2,2) — (2,2) já na fila, então pode ou não evitar duplicação (depende da implementação, vamos assumir que evita).  
Fila: (1,3),(2,2),(3,1)(1,3), (2,2), (3,1)  
Visitados: (1,1),(1,2),(2,1)(1,1), (1,2), (2,1)

---

### 🔢 **Passo 4 — Expande (1,3):**

Vizinhos válidos: (2,3)  
Fila: (2,2),(3,1),(2,3)(2,2), (3,1), (2,3)  
Visitados: (1,1),(1,2),(2,1),(1,3)(1,1), (1,2), (2,1), (1,3)

---

### 🔢 **Passo 5 — Expande (2,2):**

Vizinhos válidos: (3,2)  
Fila: (3,1),(2,3),(3,2)(3,1), (2,3), (3,2)  
Visitados: (1,1),(1,2),(2,1),(1,3),(2,2)(1,1), (1,2), (2,1), (1,3), (2,2)

---

### 🔢 **Passo 6 — Expande (3,1):**

Vizinhos válidos: (3,2) — já na fila.  
Fila: (2,3),(3,2)(2,3), (3,2)  
Visitados: (1,1),(1,2),(2,1),(1,3),(2,2),(3,1)(1,1), (1,2), (2,1), (1,3), (2,2), (3,1)

---

### 🔢 **Passo 7 — Expande (2,3):**

Vizinhos válidos: (3,3) — 🎯 **É o objetivo!**  
Fila: (3,2),(3,3)(3,2), (3,3)  
Visitados: (1,1),(1,2),(2,1),(1,3),(2,2),(3,1),(2,3)(1,1), (1,2), (2,1), (1,3), (2,2), (3,1), (2,3)

✔️ **Encontrado o objetivo (3,3)**.

---

### ✅ **Ordem de Visitação na BFS:**

(1,1),(1,2),(2,1),(1,3),(2,2),(3,1),(2,3),(3,2),(3,3)(1,1), (1,2), (2,1), (1,3), (2,2), (3,1), (2,3), (3,2), (3,3)

---

### ✅ **Caminho encontrado pela BFS (um dos possíveis caminhos mais curtos):**

(1,1)→(1,2)→(2,2)→(2,3)→(3,3)(1,1) → (1,2) → (2,2) → (2,3) → (3,3)

> 🎯 Note que esse é o mesmo caminho que você encontrou intuitivamente antes! A BFS também encontra ele como um dos caminhos ótimos.

---

---

# 🏗️ **Parte 2 – Início do Algoritmo (Template BFS)**

Aqui vai o esqueleto inicial em **Python**, super comentado:

```python
from collections import deque

# Definir o ambiente do labirinto
def get_neighbors(node):
    x, y = node
    neighbors = []
    moves = [(-1, 0), (1, 0), (0, -1), (0, 1)]  # cima, baixo, esquerda, direita

    for dx, dy in moves:
        nx, ny = x + dx, y + dy
        if 1 <= nx <= 3 and 1 <= ny <= 3:  # dentro dos limites do grid 3x3
            neighbors.append((nx, ny))
    return neighbors


def bfs(start, goal):
    queue = deque()
    queue.append([start])  # Armazena caminhos, não apenas nós
    visited = set()

    while queue:
        path = queue.popleft()  # FIFO
        node = path[-1]         # Último nó no caminho

        if node == goal:
            return path  # Caminho encontrado

        if node not in visited:
            visited.add(node)

            for neighbor in get_neighbors(node):
                new_path = list(path)
                new_path.append(neighbor)
                queue.append(new_path)

    return None  # Se não encontrar
```

---

## 🎯 Esse é um template completo da estrutura da BFS.

- 🔥 Você pode executar, testar e até expandir!
    
- Ela retorna o caminho completo desde o estado inicial até o objetivo.
    

---

# 🔍 **Busca em Profundidade (DFS)**

## 🧠 **Definição:**

A DFS explora sempre o caminho mais profundo possível antes de retroceder (backtracking). Ela tenta "mergulhar" o máximo antes de explorar outras alternativas.

---

## 🏗️ **Estrutura:**

- Usa uma **pilha (LIFO)** — último a entrar é o primeiro a sair.  
    (Simplesmente uma lista com `.append()` e `.pop()` em Python.)
    

---

## ✅ **Propriedades da DFS:**

|Propriedade|Valor|
|---|---|
|**Completude**|❌ (não garante solução se há loops ou caminhos infinitos)|
|**Ótima**|❌ (não garante caminho mais curto)|
|**Tempo**|O(bm)O(b^m)|
|**Espaço**|O(b⋅m)O(b \cdot m) — muito menor que BFS|
|**Onde:**|bb = fator de ramificação, mm = profundidade máxima do espaço de estados|

---

## 📜 **Funcionamento:**

1. Vai explorando sempre um filho (vizinho) até não poder mais (sem vizinhos ou já visitados).
    
2. Se não pode mais prosseguir, **retrocede (backtracking)** e tenta outro ramo.
    

---

## 🔥 **Vantagens:**

- Usa **muito menos memória** que BFS.
    
- Simples de implementar.
    

## ⚠️ **Desvantagens:**

- Pode ficar preso em ciclos (a menos que controle visitados).
    
- Não encontra o caminho mais curto.
    

---

## 👾 **Parte 1 – Simulação Manual da DFS no Labirinto 3x3**

### ✔️ Estado Inicial: (1,1)

### ✔️ Estado Objetivo: (3,3)

### ✔️ Ações permitidas: cima, baixo, esquerda, direita

---

### 🚦 **Execução Passo a Passo da DFS (assumindo ordem de movimentos: cima, baixo, esquerda, direita):**

> ⚠️ Na DFS, a ordem dos movimentos **muda completamente o caminho explorado**.

---

### 🔢 **Passo 0 — Estado Inicial:**

Pilha: (1,1)(1,1)  
Visitados:

---

### 🔢 **Passo 1 — Expande (1,1):**

Prioridade: cima (inválido), baixo (2,1), esquerda (inválido), direita (1,2)  
Pilha: (2,1),(1,2)(2,1), (1,2)  
Visitados: (1,1)(1,1)

_(Pegamos o último: (1,2))_

---

### 🔢 **Passo 2 — Expande (1,2):**

Vizinhos: cima (inválido), baixo (2,2), esquerda (1,1 — já visitado), direita (1,3)  
Pilha: (2,1),(2,2),(1,3)(2,1), (2,2), (1,3)  
Visitados: (1,1),(1,2)(1,1), (1,2)

_(Pega (1,3))_

---

### 🔢 **Passo 3 — Expande (1,3):**

Vizinhos: baixo (2,3)  
Pilha: (2,1),(2,2),(2,3)(2,1), (2,2), (2,3)  
Visitados: (1,1),(1,2),(1,3)(1,1), (1,2), (1,3)

_(Pega (2,3))_

---

### 🔢 **Passo 4 — Expande (2,3):**

Vizinhos: baixo (3,3) — 🎯 **Objetivo encontrado!**  
Pilha: (2,1),(2,2),(3,3)(2,1), (2,2), (3,3)  
Visitados: (1,1),(1,2),(1,3),(2,3)(1,1), (1,2), (1,3), (2,3)

---

✔️ **DFS encontrou o caminho:**  
(1,1)→(1,2)→(1,3)→(2,3)→(3,3)(1,1) → (1,2) → (1,3) → (2,3) → (3,3)

---

> 🔥 Veja que, por sorte (e pela ordem que escolhemos), o caminho é curto. Mas isso é só sorte! DFS não garante o caminho mais curto. Se tivéssemos priorizado outro vizinho, o caminho poderia ser muito mais longo.

---

## ✅ **Ordem de Visitação na DFS (com essa ordem):**

(1,1),(1,2),(1,3),(2,3),(3,3)(1,1), (1,2), (1,3), (2,3), (3,3)

---

# 🏗️ **Parte 2 – Template DFS em Python**

Aqui vai o esqueleto do algoritmo DFS bem comentado:

```python
def dfs(start, goal):
    stack = []
    stack.append([start])  # Armazena caminhos, não apenas nós
    visited = set()

    while stack:
        path = stack.pop()  # LIFO
        node = path[-1]     # Último nó no caminho

        if node == goal:
            return path  # Caminho encontrado

        if node not in visited:
            visited.add(node)

            for neighbor in get_neighbors(node):
                new_path = list(path)
                new_path.append(neighbor)
                stack.append(new_path)

    return None  # Se não encontrar
```

---

## 💡 Observação:

- **Diferença principal:**  
    → BFS usa `.popleft()` (Fila – FIFO)  
    → DFS usa `.pop()` (Pilha – LIFO)
    

---

Excelente! 🎯 Vamos para a **Busca de Custo Uniforme (UCS)** — o passo crucial antes de entrarmos no mundo da **busca informada (heurística)** como A*.

---

# 🚚 **Busca de Custo Uniforme (UCS)**

## 🧠 **Definição:**

A **UCS** (Uniform Cost Search) é uma versão da BFS que considera **custos diferentes** para transições entre estados.  
Ela sempre expande o **caminho de menor custo acumulado** até o momento.

---

## 🏗️ **Estrutura Interna:**

- Usa uma **fila de prioridade** (Priority Queue ou Min-Heap)
    
- Cada item da fila contém:  
    → o estado atual  
    → o caminho até ali  
    → o **custo acumulado**
    

---

## ✅ **Propriedades:**

|Propriedade|Valor|
|---|---|
|**Completude**|✔️ Sim, se todos os custos são ≥ 0|
|**Ótima**|✔️ Sim (melhor caminho garantido)|
|**Tempo**|O(b1+C∗ϵ)O(b^{1 + \frac{C^*}{\epsilon}})|
|Onde:||

- C∗C^* = custo da solução ótima
    
- ϵ\epsilon = menor custo de aresta possível  
    | **Espaço** | Igual ao tempo, pois armazena muitos caminhos |
    

---

## 🎯 **Diferença entre UCS e BFS:**

- **BFS:** trata todas as arestas como de custo igual (1).
    
- **UCS:** leva em conta o custo real de cada movimento (ex: terrenos, energia, distância, tempo...).
    

---

## 🔢 **Exemplo com Custos:**

Imagina um labirinto 3x3 com **custos diferentes** para cada célula.

||||
|---|---|---|
|(1,1)=1|(1,2)=5|(1,3)=1|
|(2,1)=1|(2,2)=1|(2,3)=1|
|(3,1)=9|(3,2)=1|(3,3)=1|

### 🎯 Objetivo: do (1,1) até (3,3)

Agora não basta contar os passos. Precisamos **minimizar o custo total do caminho**.

---

### 🧠 **Qual caminho UCS escolheria?**

Você quer pensar nisso antes da resposta? Ou quer que eu simule a execução da UCS passo a passo?

---

# 🏗️ **Parte 2 – Template UCS em Python (Início):**

Aqui vai a estrutura inicial da UCS com `heapq`:

```python
import heapq

def ucs(start, goal, cost_map):
    frontier = []
    heapq.heappush(frontier, (0, [start]))  # (custo_total, caminho)
    visited = set()

    while frontier:
        cost, path = heapq.heappop(frontier)
        node = path[-1]

        if node == goal:
            return path, cost  # Caminho ótimo encontrado

        if node not in visited:
            visited.add(node)

            for neighbor in get_neighbors(node):
                if neighbor not in visited:
                    new_cost = cost + cost_map.get(neighbor, 1)  # Custo da nova célula
                    new_path = list(path)
                    new_path.append(neighbor)
                    heapq.heappush(frontier, (new_cost, new_path))

    return None, float('inf')  # Se não encontrar
```

### 🧱 Suporte:

Você precisa ter um `cost_map` como dicionário:

```python
cost_map = {
    (1,1): 1, (1,2): 5, (1,3): 1,
    (2,1): 1, (2,2): 1, (2,3): 1,
    (3,1): 9, (3,2): 1, (3,3): 1
}
```

---

## 🏆 **Desafio:**

1. Com base no custo acima, simule manualmente o caminho escolhido pela UCS.
    
2. Depois podemos verificar com o algoritmo se bate!
    
---

# 🌟 **Busca A* (A Estrela)** — **Busca Heurística Informada**

---

## 🎯 **Objetivo:**

Encontrar o **caminho mais curto até o objetivo**,  
mas agora de forma **mais rápida** do que UCS,  
**usando uma heurística inteligente** que "guia" a busca.

---

## 🧠 O que é A*?

A* combina duas ideias:

- O **custo real já gasto** até um nó → `g(n)`
    
- A **estimativa do custo restante** até o objetivo → `h(n)`
    
- Soma:
    
    f(n)=g(n)+h(n)f(n) = g(n) + h(n)

Essa é a pontuação total usada para decidir quem vai ser expandido primeiro.

---

## 📦 **Componentes de A***:

|Componente|Descrição|
|---|---|
|`g(n)`|Custo real do caminho do início até `n` (igual ao UCS)|
|`h(n)`|Heurística (estimativa do custo restante de `n` até o objetivo)|
|`f(n)`|Prioridade do nó na fila de prioridade = `g(n) + h(n)`|

---

## ✅ **Propriedades do A* (com heurística admissível):**

|Propriedade|Valor|
|---|---|
|**Completude**|✔️|
|**Ótima**|✔️|
|**Tempo**|Depende da heurística|
|**Espaço**|Alto (mantém muitos caminhos)|

---

## 🔍 **Heurística Admissível:**

Uma heurística é **admissível** se **nunca superestima** o custo real até o objetivo.  
Ex: distância de Manhattan entre duas células em um grid:

h(n)=∣xatual−xobjetivo∣+∣yatual−yobjetivo∣h(n) = |x_{atual} - x_{objetivo}| + |y_{atual} - y_{objetivo}|

---

## 🔢 **Exemplo prático:**

Mesma grade 3x3 com custos:

||||
|---|---|---|
|(1,1)=1|(1,2)=5|(1,3)=1|
|(2,1)=1|(2,2)=1|(2,3)=1|
|(3,1)=9|(3,2)=1|(3,3)=1|

Heurística `h(n)` = distância de Manhattan até (3,3)

---

## 🧠 **Simulação rápida de A* para (1,1) → (3,3)**

- (1,1):
    
    - g = 0
        
    - h = |1-3| + |1-3| = 4
        
    - f = 0 + 4 = 4
        
- Quando gerar vizinhos, A* prioriza quem tem menor `f(n)`
    

Ele vai rapidamente evitar caminhos caros (como (1,2) com custo 5)  
e preferir caminhos baratos que se aproximam do destino.

---

## 💻 **Template A* em Python:**

```python
import heapq

def manhattan(a, b):
    return abs(a[0] - b[0]) + abs(a[1] - b[1])

def astar(start, goal, cost_map):
    frontier = []
    heapq.heappush(frontier, (0 + manhattan(start, goal), 0, [start]))  # (f, g, path)
    visited = set()

    while frontier:
        f, g, path = heapq.heappop(frontier)
        node = path[-1]

        if node == goal:
            return path, g  # Caminho e custo real

        if node not in visited:
            visited.add(node)

            for neighbor in get_neighbors(node):
                if neighbor not in visited:
                    new_g = g + cost_map.get(neighbor, 1)
                    h = manhattan(neighbor, goal)
                    new_f = new_g + h
                    new_path = list(path)
                    new_path.append(neighbor)
                    heapq.heappush(frontier, (new_f, new_g, new_path))

    return None, float('inf')
```

---

## 🧪 **Pronto para testar**:

- A* encontra caminhos **ótimos**
    
- Mas é **muito mais eficiente** que UCS ou BFS em mapas grandes  
    (mais rápido, menos memória, mais inteligente)
    

---

# 🧠 Resumo Geral:

|Algoritmo|Usa Custo?|Usa Heurística?|Encontra Caminho Ótimo?|
|---|---|---|---|
|**BFS**|❌ (custo = 1)|❌|✔️ (se custo uniforme)|
|**DFS**|❌|❌|❌|
|**UCS**|✔️|❌|✔️|
|**A***|✔️|✔️|✔️ (se h admissível)|

---

# 🎯 **Próxima etapa:**

Quer agora:

1. Resolver um desafio prático com A* (ex: labirinto maior)?
    
2. Avançar para **algoritmos adversariais** (como Minimax)?
    
3. Ver aplicações reais dessas buscas em IA e jogos?
    

