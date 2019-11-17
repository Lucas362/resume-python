# shell

# List Comprehension

Forma concisa de criar e manipular listas.

Sintaxe:

```
[exp for item in lista]
```

Exemplo: 

```
resultado = [numero for numero in range(10)]
```

## List Comprehension com if:

```
[exp for item in lista if cond]
```

Exemplo: 

```
resultado = [numero for numero in range(10) if numero %2 == 0]
```

### Com vários if's:

```
resultado = [numero for numero in range(100) if numero % 5 == 0 if numero % 6 == 0]
```

### Com if else

```
[resultado_if if expr else resultado_else for item in lista]
```

Exemplo:

```
esultado = ['1' if numero % 5 == 0 else '0' for numero in range(16)]
```

## Comandos úteis

* `list.append(x)`: Adiciona item ao fim da lista;
* `list.extend(iterable)`: Adiciona todos os itens do iterável *iterable* ao fim da lista. Ex:
```python
lista1 = ['azul', 'amarelo']
lista2 = ['vermelho', 'verde']
lista1.extend(lista2) # lista1 = ['azul', 'amarelo', 'vermelho', 'verde']
```
* `list.insert(i, x)`: Insere item x na posição i;
* `list.remove(x)`: remove primeiro elemento x da lista;
* `list.pop(i)`: remove item da posição i e o retona, se i não for definido, remove/retorna o último elemento;
* `list.clear()`: remove todos os elementos da lista;
* `list.index(x[, start[, end]]) ou list.index(x)`: retorna o índice do primeiro elemento cujo vlor seja x;
* `list.count(x)`: retorna o número de vezes que o valor x aparece na lista;
* `list.sort(cmp=None, key=None, reverse=False)`: ordena os itens da lista;
* `list.reverse()`: reverte os elementos da lista;
* `list.copy()`: retorna uma lista com cópia dos elementos da lista de origem.