# Dictionary

* `dict = {key:value}`: Cria um dicionário chamado dict com chaves e valores. Ex: 
```python
person = {
    "name": "Lucas",
    "Age": 22,
    "languages": [
        "python",
        "JS",
        "C",
        "Java"
    ]
}
```

* `dict[key]`: Retorna o valor associado à chave. Ex:
```python
person["name"]

Saída: 'Lucas'
```

* `dict.get(key)`: O mesmo que o anterior, ou seja, retorna o valor associado à chave. Ex:
```python
person.get("name")

Saída: 'Lucas'
```

* `dict[key] = value`: Modifica o valor associado à chave. Ex: 
```python
person["age"] = 20
```

* `for x in dict`: Loop nas chaves do dicionário. Ex:
```python
for x in person:
    print x

Saída: languages
Age
name
```

```python
for x in person:
    print person[x]

Saída: ['python', 'JS', 'C', 'Java']
22
Lucas
```

* `dict.values()`: Retorna um vetor com os valores do dicionário. Ex:
```python
person.values()

Saída: [['python', 'JS', 'C', 'Java'], 22, 'Lucas']
```

* `dict.items()`: Retorna uma vetor de tuplas contendo chave e valor. Ex:
```python
person.items()

Saída: [('languages', ['python', 'JS', 'C', 'Java']), ('Age', 22), ('name', 'Lucas')]
```

* `key in dict`: Retorna `true` caso o dicionário possua a chave, e falso caso contrário. Ex:
```python
"languages" in person

Saída: True
```

* `len(dict)`: Retorna o número de itens do docionário. Ex:
```python
len(person)

Saída: 3
```

* `dict[new_key] = value`: Adiciona uma nova chave e valor ao dicionário. Ex:
```python
person["city"] = "Luziânia"
print(person)

Saída: {
    'languages': ['python', 'JS', 'C', 'Java'], 
    'city': 'Luzi\xc3\xa2nia', 
    'Age': 22, 
    'name': 'Lucas'
}
```

* `dict.pop(key)`: Remove o item correspondente à chave especificada. Ex:
```python
person.pop("city")
print(person)

Saída: {
    "name": "Lucas",
    "Age": 22,
    "languages": [
        "python",
        "JS",
        "C",
        "Java"
    ]
}
```

* `dict.popitem()`: Remove o último elemento do dicionário;

* `del dict[key]`: Remove o item correspondente à chave especificada. Ex:
```python
del person["city"]
print(person)

Saída: {
    "name": "Lucas",
    "Age": 22,
    "languages": [
        "python",
        "JS",
        "C",
        "Java"
    ]
}
```

```python
del person
print(person)

Saída: Erro, pois o dicionário foi deletado
```

* `dict.clear()`: Esvazia o dicionário. Ex:
```python
person.clear()
print(person)

Saída: {}
```

* `dict.copy()`: Cria uma cópia do dicionário.

* `dict(dict)`: Cria uma cópia do dicionário.