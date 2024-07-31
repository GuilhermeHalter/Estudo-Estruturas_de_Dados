# Estruturas de Dados: Um Tutorial Completo

## Introdução

Estruturas de dados são formas organizadas de armazenar e gerenciar dados de maneira eficiente. Elas são fundamentais para a construção de algoritmos eficientes e desempenham um papel crucial na ciência da computação e no desenvolvimento de software.

## Tipos de Estruturas de Dados
Estruturas de dados podem ser categorizadas em duas classes principais:

**Estruturas de Dados Lineares:** Os elementos são organizados em uma sequência linear.

- Arrays
- Listas Ligadas (Linked Lists)
- Pilhas (Stacks)
- Filas (Queues)

**Estruturas de Dados Não Lineares:** Os elementos são organizados de maneira hierárquica ou em rede.

- Árvores (Trees)
- Grafos (Graphs)
- Tabelas Hash (Hash Tables)

## Estruturas de Dados Lineares
1. **Arrays (Vetores)**
Um array é uma coleção de elementos, cada um identificado por um índice ou chave. Arrays têm tamanho fixo e armazenam elementos de um tipo específico.

Exemplo em C++:

```cpp
#include <iostream>

int main() {
    // Declaração de um array
    int array[5] = {1, 2, 3, 4, 5};

    // Acesso a elementos
    std::cout << array[2] << std::endl;  // Saída: 3

    // Atualização de elementos
    array[2] = 10;
    std::cout << array[2] << std::endl;  // Saída: 10

    return 0;
}
```

2. **Listas Ligadas (Linked Lists)**
Uma lista ligada é uma coleção de nós onde cada nó contém um valor e um ponteiro para o próximo nó da lista.

Exemplo em C++:
```cpp
#include <iostream>

class Node {
public:
    int data;
    Node* next;
    Node(int data) : data(data), next(nullptr) {}
};

class LinkedList {
public:
    Node* head;
    LinkedList() : head(nullptr) {}

    void append(int data) {
        Node* new_node = new Node(data);
        if (!head) {
            head = new_node;
            return;
        }
        Node* last_node = head;
        while (last_node->next) {
            last_node = last_node->next;
        }
        last_node->next = new_node;
    }

    void print_list() {
        Node* current_node = head;
        while (current_node) {
            std::cout << current_node->data << std::endl;
            current_node = current_node->next;
        }
    }
};

int main() {
    LinkedList llist;
    llist.append(1);
    llist.append(2);
    llist.append(3);
    llist.print_list();
    return 0;
}
```

3. **Pilhas (Stacks)**
Uma pilha é uma estrutura de dados linear que segue o princípio LIFO (Last In, First Out).

Exemplo em C++:

```cpp
#include <iostream>
#include <stack>

int main() {
    std::stack<int> stack;

    // Adicionar elementos (push)
    stack.push(1);
    stack.push(2);
    stack.push(3);

    // Remover elementos (pop)
    std::cout << stack.top() << std::endl;  // Saída: 3
    stack.pop();
    std::cout << stack.top() << std::endl;  // Saída: 2
    stack.pop();

    return 0;
}
```

4. **Filas (Queues)**
Uma fila é uma estrutura de dados linear que segue o princípio FIFO (First In, First Out).

Exemplo em C++:
```cpp
#include <iostream>
#include <queue>

int main() {
    std::queue<int> queue;

    // Adicionar elementos (enqueue)
    queue.push(1);
    queue.push(2);
    queue.push(3);

    // Remover elementos (dequeue)
    std::cout << queue.front() << std::endl;  // Saída: 1
    queue.pop();
    std::cout << queue.front() << std::endl;  // Saída: 2
    queue.pop();

    return 0;
}
```

## Estruturas de Dados Não Lineares
1. **Árvores (Trees)**
Uma árvore é uma estrutura de dados hierárquica composta por nós, onde cada nó tem um valor e referências para nós filhos.

Exemplo de Árvore Binária em C++:

```cpp
#include <iostream>

class TreeNode {
public:
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int data) : data(data), left(nullptr), right(nullptr) {}
};

void inorder_traversal(TreeNode* root) {
    if (root) {
        inorder_traversal(root->left);
        std::cout << root->data << std::endl;
        inorder_traversal(root->right);
    }
}

int main() {
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    root->left->left = new TreeNode(4);
    root->left->right = new TreeNode(5);

    inorder_traversal(root);

    return 0;
}
```
2. **Grafos (Graphs)**
Um grafo é uma coleção de nós (ou vértices) e arestas que conectam pares de nós. Grafos podem ser direcionados ou não direcionados.

Exemplo de Grafo em C++ usando um dicionário (map):

```cpp
#include <iostream>
#include <vector>
#include <map>
#include <set>

void dfs(const std::map<char, std::vector<char>>& graph, char node, std::set<char>& visited) {
    if (visited.find(node) == visited.end()) {
        std::cout << node << std::endl;
        visited.insert(node);
        for (char neighbor : graph.at(node)) {
            dfs(graph, neighbor, visited);
        }
    }
}

int main() {
    std::map<char, std::vector<char>> graph;
    graph['A'] = {'B', 'C'};
    graph['B'] = {'A', 'D', 'E'};
    graph['C'] = {'A', 'F'};
    graph['D'] = {'B'};
    graph['E'] = {'B', 'F'};
    graph['F'] = {'C', 'E'};

    std::set<char> visited;
    dfs(graph, 'A', visited);

    return 0;
}
```

3. **Tabelas Hash (Hash Tables)**
Uma tabela hash é uma estrutura de dados que mapeia chaves para valores usando uma função hash.

Exemplo de Tabela Hash em C++:
```cpp
#include <iostream>
#include <unordered_map>

int main() {
    std::unordered_map<std::string, int> hash_table;

    // Adicionar elementos
    hash_table["name"] = 25;
    hash_table["age"] = 30;

    // Acesso a elementos
    std::cout << hash_table["name"] << std::endl;  // Saída: 25
    std::cout << hash_table["age"] << std::endl;   // Saída: 30

    return 0;
}
```
## Conclusão
Estruturas de dados são componentes essenciais em qualquer linguagem de programação. Compreender como usá-las e implementá-las corretamente é crucial para a criação de algoritmos eficientes e soluções eficazes para problemas complexos.

Aprofunde-se nesses conceitos, pratique a implementação de cada estrutura de dados e explore suas aplicações em projetos reais para se tornar um programador mais competente e versátil.
