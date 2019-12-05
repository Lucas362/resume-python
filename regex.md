# RegEx

* `.`: Corresponde a qualquer caracter exceto `newline`. Se a flag `DOTALL` for especificada, corresponde a qualquer letra inclusive `newline`. Ex:
```python
import re

str = "hello world"

#Search for a sequence that starts with "he", followed by two (any) characters, and an "o":

x = re.findall("he..o", str)
print(x)

Saída: ['hello']
```

* `^`: (começa com)Se colocado no início da classe, retorna tudo menos o primeiro caracter. No modo `MULTILINE` faz correspondência a todo início de linha;
```python
import re

str = "hello world"

#Check if the string starts with 'hello':

x = re.findall("^hello", str)
if (x):
  print("Yes, the string starts with 'hello'")
else:
  print("No match")

Saída: "Yes, the string starts with 'hello'"
```

* `$`: (termina com)Corresponde ao fim da string ou exatamente antes de `newline`no fim da string, e no modo `MULTILINE` também corresponde antes de uma `newline`. Ex:
```python
import re

str = "hello world"

#Check if the string ends with 'world':

x = re.findall("world$", str)
if (x):
  print("Yes, the string ends with 'world'")
else:
  print("No match")

Saída: "Yes, the string ends with 'world'"
```

* `*`: Zero ou mais correspondências. Ex:
```python
import re

str = "The rain in Spain falls mainly in the plain!"

#Check if the string contains "ai" followed by 0 or more "x" characters:

x = re.findall("aix*", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['ai', 'ai', 'ai', 'ai']
"Yes, there is at least one match!"
```

* `+`: Uma ou mais correspondências. Ex:
```python
import re

str = "The rain in Spain falls mainly in the plain!"

# Check if the string contains "ai" followed by 1 or more "x" characters:

x = re.findall("aix+", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: []
"No match"
```

* `?`: Zero ou uma correpondências à esquerda. Ex:
```python
import re

str = "The rain in Spain falls mainly in the plain!"

# Check if the string contains "ai" followed by 0 or 1 "x" characters:

x = re.findall("aix?", str)

print(x)

Saída: ['ai', 'ai', 'ai', 'ai']
```

* `*?, +?, ??`: Os qualificadores `*`, `+` e `?` são ambiciosos, ou seja, correspondem a tantos textos quanto possível, com o acréscimo do `?` ao invés de retorna toda a string, retorna somente a correspondencia.

* `{m}`: Exatamente o número de correnpondencias espcificado (m). Ex:
```python
import re

str = "The rain in Spain falls mainly in the plain!"

#Check if the string contains "a" followed by exactly two "l" characters:

x = re.findall("al{2}", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['all']
"Yes, there is at least one match!"
```

* `{m,n}`: O número de repetições entre m e n (incluindo os extremos);

* `{m,n}?`: Funciona como `{m,n}`, porém sempre corresponderá ao menor possível;

* `\`: Usado para uma sequència especial, ou para ignorar caracteres especiais (`*`, `?`, podem pertencer à string, por exemplo). Ex:
```python
import re

str = "That will be 59 dollars"

#Find all digit characters:

x = re.findall("\d", str)
print(x)

Saída: ['5', '9']
```

* `[]`: Conjunto de caracteres, individualmente como `[amk]` que correspondem a `a`, `m` ou `k`, ou em conjunto como `[a-z]` que corresponde a todos as letras minúsculas entre a e z (incluindo os extremos). Ex:
```python
import re

str = "The rain in Spain"

#Find all lower case characters alphabetically between "a" and "m":

x = re.findall("[a-m]", str)
print(x)

Saída: ['h', 'e', 'a', 'i', 'i', 'a', 'i']
```

* `|`: Equivalente a `ou`. Ex:
```python
import re

str = "The rain in Spain falls mainly in the plain!"

#Check if the string contains either "falls" or "stays":

x = re.findall("falls|stays", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['falls']
"Yes, there is at least one match!"
```

* `()`: Indica um grupo de expressões regulares;

## Sequências especiais

* `\A`: Corresponde se os caracteres especificados estiverem no início da string. Ex:
```python
import re

str = "The rain in Spain"

#Check if the string starts with "The":

x = re.findall("\AThe", str)

print(x)

if (x):
  print("Yes, there is a match!")
else:
  print("No match")

Saída: ['The']
"Yes, there is a match!"
```

* `\b`: Checa a correspondencia no início ou no final de acordo com o local colocado. Ex:
```python
import re

str = "The rain in Spain"

#Check if "ain" is present at the beginning of a WORD:

x = re.findall(r"\bain", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: []
"No match"
```

```python
import re

str = "The rain in Spain"

#Check if "ain" is present at the end of a WORD:

x = re.findall(r"ain\b", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['ain', 'ain']
"Yes, there is at least one match!"
```

* `\B`: O oposto de `\b`, literalmente o contrário, ou seja, retorna caso não esteja no início ou no fim, de acordo com o local escolhido. Ex:
```python
import re

str = "The rain in Spain"

#Check if "ain" is present at the beginning of a WORD:

x = re.findall(r"\Bain", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['ain', 'ain']
"Yes, there is at least one match!"
```

```python
import re

str = "The rain in Spain"

#Check if "ain" is present at the end of a WORD:

x = re.findall(r"ain\B", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: []
"No match"
```

* `\d`: Corresponde onde possui dígitos (números entre 0 e 9), equivale a `[0-9]`. Ex:
```python
import re

str = "The rain in Spain"

#Check if the string contains any digits (numbers from 0-9):

x = re.findall("\d", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: []
"No match"
```

* `\D`: O oposto de `\d`, ou seja, retorna correpondência em todos os caracteres não decimais, equivale a `[^0-9]`. Ex:
```python
import re

str = "The rain in Spain"

#Return a match at every no-digit character:

x = re.findall("\D", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['T', 'h', 'e', ' ', 'r', 'a', 'i', 'n', ' ', 'i', 'n', ' ', 'S', 'p', 'a', 'i', 'n']
"Yes, there is at least one match!"
```

* `\s`: Corresponde a caracteres de espaço em branco e tabulação, equivalente a `[ \t\n\r\f\v]`. Ex:
```python
import re

str = "The rain in Spain"

#Return a match at every white-space character:

x = re.findall("\s", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: [' ', ' ', ' ']
"Yes, there is at least one match!"
```

* `\S`: O contrário de `\s`, ou seja, corresponde a todos os caracteres que não são espaço em branco ou se tabulação, equivale a `[^ \t\n\r\f\v]`. Ex:
```python
import re

str = "The rain in Spain"

#Return a match at every NON white-space character:

x = re.findall("\S", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['T', 'h', 'e', 'r', 'a', 'i', 'n', 'i', 'n', 'S', 'p', 'a', 'i', 'n']
"Yes, there is at least one match!"
```

* `\w`: Correponde a todos os caracteres que formam uma palavra (letras e números), equivale a `[a-zA-Z0-9_]`. Ex: 
```python
import re

str = "The rain in Spain"

#Return a match at every word character (characters from a to Z, digits from 0-9, and the underscore _ character):

x = re.findall("\w", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: ['T', 'h', 'e', 'r', 'a', 'i', 'n', 'i', 'n', 'S', 'p', 'a', 'i', 'n']
"Yes, there is at least one match!"
```

* `\W`: O oposto de `\w`, ou seja, retorna todos os caracteres que não fazem parte da palavra, equivale a `[^a-zA-Z0-9_]`. Ex:
```python
import re

str = "The rain in Spain"

#Return a match at every NON word character (characters NOT between a and Z. Like "!", "?" white-space etc.):

x = re.findall("\W", str)

print(x)

if (x):
  print("Yes, there is at least one match!")
else:
  print("No match")

Saída: [' ', ' ', ' ']
"Yes, there is at least one match!"
```

* `\Z`: Corresponde somente caso os caracteres especificados estejam no final da palavra. Ex:
```python
import re

str = "The rain in Spain"

#Check if the string ends with "Spain":

x = re.findall("Spain\Z", str)

print(x)

if (x):
  print("Yes, there is a match!")
else:
  print("No match")

Saída: ['Spain']
"Yes, there is a match!"
```

## Functions

* `findall()`: Retorna uma lista contendo todas as correspondências. Ex:
```python
import re

#Return a list containing every occurrence of "ai":

str = "The rain in Spain"
x = re.findall("ai", str)
print(x)


Saída: ['ai', 'ai']
```

* `search()`: Procura a string que corresponde e retorna um `Match object`. Se possuir mais de um match, retorna somente o primeiro. Ex:
```python
import re

str = "The rain in Spain"
x = re.search("\s", str)

print("The first white-space character is located in position:", x.start())

Saída: "The first white-space character is located in position: 3"
```

 - `Obs`: O `Match object` possui os seguintes atributos e métodos:
    - end, 
    - endpos, 
    - expand, 
    - group, 
    - groupdict, 
    - groups, 
    - lastgroup, 
    - lastindex, 
    - pos, 
    - re, 
    - regs, 
    - span, 
    - start, 
    - string

* `split()`: Retorna uma lista contendo a string que recebeu o `split`. Ex:
```python
import re

#Split the string at every white-space character:

str = "The rain in Spain"
x = re.split("\s", str)
print(x)

Saída: ['The', 'rain', 'in', 'Spain']
```

Possui o parâmetro `maxsplit` que pode especificar o número de ocorrências. Ex:
```python
import re

#Split the string at the first white-space character:

str = "The rain in Spain"
x = re.split("\s", str, 1)
print(x)

Saída: ['The', 'rain in Spain']
```

* `sub()`: Substitui todas as ocorrências pelo valor escolhido. Ex:
```python
import re

#Replace all white-space characters with the digit "9":

str = "The rain in Spain"
x = re.sub("\s", "9", str)
print(x)

Saída: "The9rain9in9Spain"
```

Possui o parâmetro `count` que pode especificar o número de substituições. Ex:
```python
import re

#Replace the first two occurrences of a white-space character with the digit 9:

str = "The rain in Spain"
x = re.sub("\s", "9", str, 2)
print(x)

Saída: "The9rain9in Spain"
```

* `Match object`: É um objeto que contém informações sobre o resutado de `search()`. Ex:
```python
import re

#The search() function returns a Match object:

str = "The rain in Spain"
x = re.search("ai", str)
print(x)

Saída: <_sre.SRE_Match object; span=(5, 7), match='ai'>
```

Este possui 3 principais métodos:
  - `span()`: retorna uma tupa contendo a posição de início e de fim da correspondência;
  - `string`: retorna a string passada na função;
  - `group()`: retorna a parte da string onde há a correspondência.

Ex:
```python
import re

#Search for an upper case "S" character in the beginning of a word, and print its position:

str = "The rain in Spain"
x = re.search(r"\bS\w+", str)
print(x.span())

Saída: (12, 17)
```

```python
import re

#The string property returns the search string:

str = "The rain in Spain"
x = re.search(r"\bS\w+", str)
print(x.string)

Saída: "The rain in Spain"
```

```python
import re

#Search for an upper case "S" character in the beginning of a word, and print the word:

str = "The rain in Spain"
x = re.search(r"\bS\w+", str)
print(x.group())

Saída: "Spain"
```
