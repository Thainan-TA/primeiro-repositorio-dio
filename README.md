# primeiro-repositorio-dio
Desafio de projeto - realizando primeiro repositório no GitHub

## Links úteis
[Sintaxe básica markdown](https://www.markdownguide.org/basic-syntax/)

[Conhecendo o Python](https://www.python.org/doc/)

[Funções estatísticas no Python](https://docs.python.org/pt-br/3/library/statistics.html)



Exemplo de obtenção e interpretação de um valor-p

Você quer determinar se um novo aditivo da gasolina tem um efeito sobre o consumo de combustível. Se a milhagem de gás conhecida para essa classe específica de carros é de 25 milhas por galão (mpg), as hipóteses para este estudo são H0: μ = 25 e HA: μ ≠ 25.

Obtenção de valor-p com um teste t com 1 amostra
Você testa 35 carros e descobre que o consumo dos carros varia de 14,4 a 28,8. Após colocar os dados na coluna MPG, você executa o teste t do Minitab (comando de menu Estat > Estatísticas Básicas > Teste t para 1 Amostra ou o comando de sessão TTEST) e obtém os seguintes resultados:

Teste T para Uma Amostra: C1



Estatísticas Descritivas

                                IC de 95% para
 N   Média  DesvPad  EP Média          μ
35  23,657    3,416     0,577  (22,484; 24,831)

μ: média de C1

Teste

Hipótese nula         H₀: μ = 25
Hipótese alternativa  H₁: μ ≠ 25


Valor-T  Valor-p
  -2,33    0,026


Estatística

Exemplo: teste de hipótese com P-valor

from scipy import stats
import numpy as np

#valor de alpha, que é uma probabilidade
alpha = 0.01

#cálculo dos valores críticos, relativos à alpha/2 e 1-alpha/2
valor_critico_1 = stats.norm.ppf(alpha/2)
valor_critico_2 = stats.norm.ppf(1 - alpha/2)

print(valor_critico_1)
print(valor_critico_2)

Desafio 1: automatizar teste de hipóteses
Desafio 1: crie um programa Python que automatiza o teste de hipóteses para o caso do exemplo 2, em que se espera um valor fixo para a média. O programa deve receber os dados de média populacional, desvio padrão populacional, nível de significância alpha, número de elementos da amostra e média da amostra. Ao final, deve imprimir “Rejeito H0” ou “Não rejeito H0”, dependendo do resultado do teste de hipóteses.

m = 50 #Média populacional
std = 2 #Desvio padrão populacional
alpha = 0.05 
n = 25 #Número de amostras
x_amostra = 51.3 #Média amostral

import math    

z_score = (x_amostra - m)/(std/math.sqrt(n))

print(z_score)

from scipy import stats

#cálculo dos valores críticos, relativos à alpha/2 e 1-alpha/2
valor_critico_1 = stats.norm.ppf(alpha/2)
valor_critico_2 = stats.norm.ppf(1 - alpha/2)

print(valor_critico_1) 
print(valor_critico_2)

if valor_critico_1 < z_score and z_score < valor_critico_2:
    print('Não rejeito H0')
else:
    print('Rejeito H0')

#Desafio 2: selecionar 10.5 % dos alunos na hora

z = stats.norm.ppf(0.105)

print(z)

import numpy as np

mu, sigma = 0, 1 # mean and standard deviation
s = np.random.normal(mu, sigma)
print(s)

if s < z:
    print('Escolhido')
else:
    print('Não escolhido')
