<p>As linguagens de programação oferecem diferentes maneiras de armazenar e acessar dados. Exemplos comuns são as arrays, listas, mapas, entre outros.</p>

<p>Através delas, armazenamos os elementos em localizações de memória contínua, ou seja, qualquer elemento em uma Array pode ser localizado em tempo constante O(1), com menor complexidade e, consequentemente, oferecendo rapidez e possibilitando o menor tempo de busca possível. Isso é, enquanto soubermos examente o index do elemento que queremos localizar.</p> 

<p>Mas e em cenários onde não sabemos o quanto de memória está sendo alocada? Por exemplo, em uma aplicação podemos presumir que um milhão de inputs seja o suficiente para cada usuário alocar em uma Array. Mas e se esse usuário só precisar de 20% desse espaço? Vamos estar desperdiçando bastante memória.</p>

<p>Quando lidamos com dados dinâmicos onde precisamos inserir, realocar ou deletar um elemento no início ou no meio dessa Array também é um desafio, pois precisaríamos checar se tem espaço para esse novo elemento, realocar todos os outros e isso definitivamente demandaria tempo, paciência e riscos.</p>


### <b>O que é uma Linked List e como ela pode solucionar isso?</b>

<p>Linked List é uma estrutura de dados linear composta por várias células, formando uma lista encadeada ou "chain", onde se é armazenado um conjunto de nós (nodes) ligados um ao outro, formando uma sequência dinâmica.</p>

![alt text](https://codeforwin.org/wp-content/uploads/2015/09/Linked-list-nodes.png)

- Os elementos podem ser inseridos e removidos em tempo constante.
- Não desperdiça memória com o que não é utilizado.

### <b>Quando usar uma Linked List?</b>

- Quando você não sabe a quantidade de itens na Array.
- Quando você não precisa de acesso aleatório aos elementos (diferente da Array, aqui você não consegue acessar o elemento partindo do index).
- Quando você está lidando com dados dinâmicos e precisa inserir, deletar ou realocar elementos.


---

## Impletementação da classe Node

Como ilustrado na imagem acima, temos em mente que o objeto Node tem
duas partes principais: um valor e o endereço.

Para que a Linked List seja criada, ela precisa conter pelo menos um
valor. Posteriormente o definiremos como nulo.

Uma observação importante é que o valor None representa que, de fato,
não existe um próximo objeto Node.


``` python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
```


Agora vamos definir algumas funções básicas, sendo elas:

     | insert_node_to_tail(node)  | Para inserir um novo elemento após o último nó da lista.   | 
     | insert_node_to_head(node)  | Para inserir um novo elemento como o primeiro nó da lista. | 
     | is_empty()                 | Checa se a lista está vazia.                               | 
     | head()                     | Retorna o primeiro elemento da lista.                      | 
     | tail()                     | Retorna o último elemento da lista.                        | 



``` python
class LinkedList:                            # Primeiro passo | Criando a classe e indentando o primeiro node nulo (Head) 
    def __init__(self):
        self.head = Node(None)

    def insert_node_to_tail(self, node):    # Terceiro passo | Inserindo o ultimo node (Tail)
        self.tail().next = node

    def insert_node_to_head(self, node):    # Quarto passo | Inserindo o primeiro node (Head). Caso possua algum elemento após ao nulo que já definimos, 
                                            # será criado um novo elemento e, após ele, é inserido nosso elemento 1 de Head. ex: elem0 (self.head) -> novo_elemento (node.next) -> elemento1 (head_element.next)
        if self.head.next:                    
            head_element = self.head
            node.next, head_element.next = head_element.next, node
        else:
            self.head.next = node           # elem0 -> novo_elemento

    def is_empty(self):                       # Sexto passo | Checando se o novo_elemento é nulo
        return self.head.next is None

    def head(self):                           # Quinto passo | Retornando o Head (elemento 1)
        return self.head.next

    def tail(self):                           # Segundo passo | Caso não possua próximo elemento, é retornado o head. Caso possua, é retornado o ultitmo (tail).
        pointer = self.head
        while pointer.next:                   
            pointer = pointer.next
        return pointer
        
```


------------------------------------------------------------------------

<p>E é isso! Implementamos nossa Linked List com suas funções básicas, além
de entendermos quando usar e também quais problemas ela resolve.</p>

<p>Espero que tenham curtido e aprendido um pouco mais sobre estrutura de
dados. Até a próxima!</p>

------------------------------------------------------------------------

Ian Sobral

[Meu Linkedin](https://www.linkedin.com/in/ian-sobral-0b54701a9/)



``` python
# Bibliografia e referências:
# Desafio https://www.youtube.com/mycodeschool
# Artigo https://medium.com/real-algorithms/linked-list-c-python-776ee340a357
# Artigo https://www.happycoders.eu/algorithms/array-vs-linked-list/
# Artigo https://medium.com/real-algorithms/linked-list-c-python-776ee340a357

```

