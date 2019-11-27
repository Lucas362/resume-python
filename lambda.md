# Lambda

Lambda são funções anônimas, ou seja, que não possuem nome, e utilizam ```lambda``` e não ```def``` como prefixo. E pode possuir vários argumentos, porém somente um expressão.

Sintaxe:
```
lambda argumento_1,...,argumento_n: expressão
```

Estas funções funcionam da mesma forma que funções convencionais.

Em sintese, funções lambdas podem ser entendidas em três pontos: 

 - Uma função lambda sempre executa uma única expressão

 - Uma expressão é um código python que roda através de uma função lambda, que pode ou não ter algum valor de retorno

 - Uma função lambda pode receber qualquer número de argumentos de entrada e retornar qualquer número de argumentos, desde que a função possua uma única expressão.

Ex:

```python
add = lambda a: a + a
print(add(20))

Saída: 40
```