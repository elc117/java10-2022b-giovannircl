# java10-2022b-giovannircl
java10-2022b-giovannircl created by GitHub Classroom

## Explicação da execução do código _sharedaccount_:

### Análise (sem o syncronized):

- Uma conta é criada com o saldo = 100:
```
    float saldoInicial = 100f;
    Conta c = new Conta(saldoInicial);
```

- Duas threads são criadas, uma depositando 1000 na conta, e outra retirando 250 da conta:
```
    ThreadDeposita td = new ThreadDeposita(c, 10, 100f);
    ThreadRetira tr = new ThreadRetira(c, 5, 50f);
```
- A partir do momento em que se da o join nessas threads, elas rodam de maneira concorrente manipulando
o saldo (com as funções de retirar e depositar), ou seja, enquanto a thread que deposita adiciona 1000 aos 100 inicial,
a thread que retira o saldo utiliza o valor no meio da execução da outra thread (que no caso em questão é 1000). 
Portanto, ao invés de subtrair 250 de 1100 que seria o correto, ela acaba por subtrair 250 dos 1000:

![image](https://user-images.githubusercontent.com/60160232/200311384-47c8e3f1-6b62-460a-8143-1017021a8453.png)

### Pergunta::

- Acredito que o material esteja bem completo para sanar quaisquer dúvidas. Teve um assunto bem específico que eu realmente tive dificuldade
que foi em herdar de uma classe "pai" utilizando threads. Não entendi se devo fazer com que a classe principal dê um _extends Thread_ ou se as
filhas devem fazer isso e a classe "pai" apenas conter as características para serem herdadas.

- Na minha visão é necessário ter uma classe pai que extende Thread, ou implementa Runnable e as filhas herdam dela, podendo ser threads que apenas têm suas peculiaridades














