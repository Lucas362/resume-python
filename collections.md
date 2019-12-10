# Collections

* `ChainMap(*maps)`: Classe provida para linkar rapidamente um número de mapeamentos então eles podem ser tratados como uma unidade. Isto é mais rápido que criar um novo dicionário e rodar múltiplas chamadas `update()`.

    Um `ChainMap` agrupa múltiplos dicionários ou outros mapeamentos juntos para criar uma única e "updatable" view. Ex:

```python
from collections import ChainMap

defaults = {'color': 'red', 'user': 'guest'}
setted = {'main': 'no', 'guest': 'true'}

combined = ChainMap(setted, defaults)
print(combined)
print(combined['color'])

Saída: ChainMap({'main': 'no', 'guest': 'true'}, {'color': 'red', 'user': 'guest'})
'red'
```

Alguns atributos do `ChainMap` são:

- `maps`: Acessa os dicionários ou outros elementos mapeados. Sintaxe: `map.maps[index]`.
- `new_child`: Cria um novo "filho" (elemento mapeado) vazio ao início do map. Sintaxe: `map.new_child()`.
- `parents`: Retorna todos os elementos do map, exceto o primeiro. Sintaxe: `map.parents`.

    É possível herdar de `ChainMap` e utilizá-lo de forma mais apropriada a depender do contexto (ChainMap só realiza updates na primeira cadeia do mapeamento). Ex:

```python
class DeepChainMap(ChainMap):
    def __setitem__(self, key, value):
        for mapping in self.maps:
            if key in mapping:
                mapping[key] = value
                return
        self.maps[0][key] = value

    def __delitem__(self, key):
        for mapping in self.maps:
            if key in mapping:
                del mapping[key]
                return
        raise KeyError(key)

d = DeepChainMap({'zebra': 'black'}, {'elephant': 'blue'}, {'lion': 'yellow'})
d['lion'] = 'orange'
d['snake'] = 'red'
del d['elephant']
print(d)
DeepChainMap({'zebra': 'black', 'snake': 'red'}, {}, {'lion': 'orange'})
```

* `Counter`: Ferramenta para contar "hashable" objects. Ex: 
```python
from collections import Counter

count = Counter(['red', 'blue', 'red', 'green', 'blue', 'blue'])
print(count)
print(count['blue'])

Saída: Counter({'blue': 3, 'red': 2, 'green': 1})
3
```

Alguns atributos do `Counter` são:

- `elements()`: Retorna um iterator com os elementos repetidos tantas vezes quanto o original. Sintaxe: `count.elements()`.
- `most_common([n])`: Retorna um lista com os `n` elementos mais comuns, do mais comum para o menos comum. Sintaxe: `count.most_commom(n)`.
- `subtract([iterable-or-mapping])`: Subtrai o número de repetição de um item com relação o número de repetições do mesmo item em um outro counter. Sintaxe: `count.subtract(count2)`.
- `update([iterable-or-mapping])`: Funciona como o `dict.update()`.

* `deque`: Retorna uma lista com o desenfileiramento do iterable. Ex:

```python
from collections import deque

d = deque('ghi')
print(d)

Saída: deque(['g', 'h', 'i'])
```

Alguns métodos do `deque`:

- `append(x)`: Adiciona o elemento x ao fim da lista.
- `appendleft(x)`: Adiciona o elemento x ao início da lista.
- `clear()`: Remove todos os elementos da lista.
- `copy()`: Cria uma cópia da lista.
- `count(x)`: Conta a quantidade de elementos da lista iguais a x.
- `extend(iterable)`: Adiciona vários elementos ao fim da lista.
- `extendleft(iterable)`: Adiciona vários elementos ao início da lista. Inverte a posição original do iterable.
- `index(x[,start[,stop]])`: Retorna a posição da primeira ocorrência do elemento x. Retorna exceção caso não encontre.
- `insert(i, x)`: Insere o elemento x na posição i.
- `pop()`: Remove e retorna o último elemento da lista.
- `popleft()` Remove e retorna o primeiro item da lista.
- `remove(value)`: Remove a primeira ocorrência do valor.
- `reverse()`: Inverte os elementos da lista.
- `rotate(n=1)`: Rotaciona a lista n vezes. Ex:
```python
from collections import deque

d = deque('1234567')
print(d)

d.rotate(1)
print(d)

Saída: deque(['1', '2', '3', '4', '5', '6', '7'])
deque(['7', '1', '2', '3', '4', '5', '6'])
```

- `maxlen`: Tamanho máximo de uma `deque`.

* `defaultdict`: Sobresceve o `dict` em um método e adiciona uma variável. As funcionalidades restantes são iguais ao `dict`, que são `__missing__(key)` e `default_factory`.

* `namedtuple()`: Permite o uso de tuplas de forma mais legível e auto-documentada. Podem ser utilizadas em qualquer lugar que tuplas normais são utilizadas. Ex:
```python
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(11, y=12)
print(str(p[0]) + ' - ' + str(p[1]))
print(str(p.x) + ' - ' + str(p.y))
print(p)

Saída: 11 - 12
11 - 12
Point(x=11, y=12)
```

Alguns métodos do `namedtuple`são:

- `_make(iterable)`: Cria uma nova instância a partir de uma sequência ou iterable. Sintaxe: `somenamedtuple._make(iterable)`.
- `_asdict()`: Retorna um `dict` com campos mapeados correspondendo aos valores. Sintaxe: `somenamedtuple._asdict()`.
- `_replace(**kwargs)`: Retorna uma nova instância da `namedtuple` substituindo os campos especificados.
- `_fields`: Tupla de strings listando os nosmes dos campos. Sintaxe: `somenamedtuple._fields`.
- `_field_defaults`: Dicionário que mapeia os nomes dos campos e seus valores padrão.

* `OrderedDict`: Funciona como o `dict`, porém possui métodos de reordenação melhores. Os métodos extras são `popitem(last=True)` e `move_to_end(key, last=True)`.

* `UserDict`: Simula um dicionário, mas pode sobrescrever os métodos para odificar a forma como o `dict` lida com as chaves e valores. Ex:
```python
class Pins(UserDict):

    def __contains__(self, key):
        return str(key) in self.keys()

    def __setitem__(self, key, value):
        self.data[str(key)] = value

pins = Pins(one=1)
pins[3] = 1
print(pins)

Saída: {'one': 1, '3': 1}
```

* `UserList`: Está para a lista ssim como o `UserDict` está para o `dict`. Olhar a seção `UserDict`.

* `UserString`: Está para a stringssim como o `UserDict` está para o `dict`. Olhar seção `UserDict`.
