# String 

* `str.capitalize()`: retorna uma cópia da string com o primeiro caracter maiúsculo;

* `str.center(width[, fillchar])`: retina uma string centralizada com o tamanha *width*. Ex:
```
string = "okok"
string.center(25)
Saída: '          okok           '

string = "okok"
string.center(25, '@')
Saída: '@@@@@@@@@@okok@@@@@@@@@@@'
```

* `str.count(sub[,start[,end]])`: conta as ocorrências de uma substring dentre da string. Ex:
```
str = 'teste de string'
str.count('te')

Saída: 2
```

* `str.decode([enconding[,errors]])`: Retorna o contrário do encode. Ex:
```
string = "this is a string example...wow!!!"
string = string.encode('base64', 'strict')

print "Encoded String: " + string
print "Decoded String: " + string.decode('base64', 'strict')

Resultado:

Encoded String: dGhpcyBpcyBzdHJpbmcgZXhhbXBsZS4uLi53b3chISE=
Decoded String: this is string example....wow!!!
```

* `str.encode([encoding[, errors]])`: Retorna uma versão encode da string;

* `str.endswith(suffix[,start[,end]])`: retorna `true` se a string terminar com o *suffix* e `false` caso contrário;

* `str.expandtabs([tabsize])`: usa `\t` para tabular texto. Ex:
```
'01\t012\t0123\t01234'.expandtabs()
Saída: '01      012     0123    01234'
```

* `str.find(sub[,start[,end]])`: Menor index da substring `sub` na string (retorna -1 se não achar a substring na string). Ex:
```
str = 'teste de string'
str.find('str')

Saída: 9
```

* `str.format(*args, **kwargs)`: Formata a string. Ex:
```
"The sum of 1 + 2 is {0}".format(1+2)

Saída: The sum of 1 + 2 is 3
```

* `str.index(sub[,start[,end]])`: Que nem o `find()` mas dá erro se não achar a substring;

* `str.isalnum()`: Retorna `true` se todos os caracteres forem alfanuméricos e tiver ao menos um caracter, e `falso` caso ao menos um não seja;

* `str.isalpha()`: Retorna `true` se todos os caracteres forem alfabéticos e tiver ao menos um caracter, e `falso` caso contrário;

* `str.isdigit()`: Retorna `true` se todos os caracteres forem dígitos e tiver ao menos um caracter, e `false` caso contrário;

* `str.islower()`: Retorna `true` caso a String seja minúscula, e `falso` caso contrário;

* `str.isspace()`: Retorna `true` caso a String seja feita somente de espaços, e `falso` caso contrário;

* `str.istitle()`: Retorna `true` caso a String seja formatada como título, e `falso` caso contrário;

* `str.join(iterable)`: Retorna a concatenção das duas strings;

* `str.ljust(width[,fillchar])`: Justifica o texto a esquerda (com o caracter que escolher, o padrão é espaço). Retorna `str` caso o tamanho seja menos que a string;

* `str.lower()`: Retorna uma cópia da string com os caracteres minúsculos;

* `str.lstrip([chars])`: Retorna uma cópia da string que está após o caracter escolhido. Ex: 
```
'   spacious   '.lstrip()
Saída: 'spacious   '

'www.example.com'.lstrip('cmowz.')
Saída: 'example.com'
```

* `str.partition(sep)`: Separa a string em um 3-tupla, na posição da primeira ocorrência de `sep` na string. Ex:
```
txt = "I could eat bananas all day"
print(txt.partition("bananas"))

Saída: ('I could eat ', 'bananas', ' all day')
```

* `str.replace(old,new[,count])`: Retorna uma cópia da string substituindo `old` por `new`. E possui o parametro opcional `count` que substitui somente a quantidade pedida de ocorrências;

* `str.rfind(sub[,start[,end]])`: Retorna a última posição em que a substring é encontrada na string;

* `str.rindex(sub[,start[,end]])`: Igual ao `rfind()`, mas retorna erro quando a substring não é encontrada;

* `str.rjust(width[,fillchar])`: Justifica o texto a direita (com o caracter que escolher, o padrão é espaço). Retorna `str` caso o tamanho seja menos que a string;

* `str.rpartition(sep)`: Igual ao `partition(sep)`, mas retorna vazio à direita caso não encontre o sep;

* `str.rsplit([sep[,maxsplit]])`: Funciona como o `split([sep[, maxsplit]]])`, com a diferença do split à direita;

* `str.rstrip([chars])`: Retorna uma cópia da string removendo a última ocorrência do caracter. Ex: 
```
'   spacious   '.rstrip()

Saída: '   spacious'


'mississippi'.rstrip('ipz')

Saída: 'mississ'
```

* `str.split([sep[,maxsplit]])`: Faz o split da string. Se `sep` não for definido o caracter espaço será o separador, e o `maxsplit` define o máximo de splits que ocorrerão na string;

* `str.splitlines([keepends])`: Faz o split baseado em `\n`, `\r` e `\r\n`;

* `str.startswith(prefix[,start[,end]])`: Retorna `true` caso a string comece com o `prefix`, e falso caso contrário;

* `str.strip([chars])`: Remove os caracteres escolhidos da string. Ex: 
```
'   spacious   '.strip()

Saída: spacious


'www.example.com'.strip('cmowz.')

Saída: example
```

* `str.swapcase()`: Retorna uma cópia da string, caso seja maiúscula fica minúscula, e vice-versa;

* `str.title()`: Retorna string com primeiro caracter de cada palavra maiúsculo, e o resto minúsculo;

* `str.translate(table[,deletechars])`: Retorna uma cópia da string removendo os caracteres selecionados e mapeia os caracteres restantes;

* `str.upper()`: Retorna uma cópia maiúscuka da string;

* `str.zfill(width)`: Completa a string à esquerda com 0.