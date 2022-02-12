Bom dia professor, o nosso grupo e composto pelos elementos



Neste trabalho, realizamos uma implementacao do algoritmo de Gordon, para gerar um numero primo forte.
Vamos continuar com a apresentacao, e explicacao da nossa implementacao.

Comecamos por definir o tamanho do numero primo a ser gerado, neste caso, pretendemos um numero com aproximadamente 512 bits.
De seguida geramos dois numeros primos aleatotios, denominados s e t, utilizando a funçao pre-definida randomprime, o tamanho destes primos será 256 bits, pois o número gerado irá ter o dobro do tamanho destes dois numeros iniciais.

Seguidamente, a partir da seleção de um inteiro i procuramos o primeiro numero primo, na sequência definida por 2it+1, i=1, i=2, continuando para i igual ao i anterior mais 1.

Agora proseguimos para o calculo do dobro da congruencia de s^*(r-2) base r, multiplicando por s menos 1. Este valor sera o p0.

Finalmente, selecionando um inteiro j, a semelhanca da selecao do inteiro i no segundo passo, procuramos o primeiro primo, na sequencia p0+2jrs, com o p0 definido no passo anterior, o r calculado no segundo passo, e s um dos primos inicialmente gerados.
O resultado deste calculo sera o primo forte gerado pelo algoritmo.
Podemos observar que o resultado obtido tem um tamanho de ....... bits


Para confirmar o funcionamento da nossa implementacao, vamos verificar se o numero p cumpre os requesitos da definicao de numero primo forte.
Pela definicao criptografica, com a funcao pre-definida factor, realizamos a fatorizacao em numeros primos de p-1, que como podemos ver tem um grande fator primo, este valor sera guardo como rp. O mesmo sera feito para p+1 e para rp - 1, podemos ver que todas estas fatorizacoes, contem um fator grande, cumprindo assim a definicao de primo forte.






A prova anterior, devido a dificuldade do calculo de fatorizacao, fomos obrigados a utilizar um numero primo mais pequeno do que o esperado, para ser possivel computar a prova em tempo util para numeros superiores, utilizamos o proximo metodo de verificacao mais eficiente, feita com base no teorema de fermat.

Sendo s e r numeros primos distintos. Pelo teorema de Fermat, como s^r-1 == 1 mod r, podemos concluir que p0=1 mod r, e p0 = -1 mod s.
Uma vez que pelo algoritmo de Gordon, p = p0+2jrs, basta verificar que p0+2jrs-1 = 0 mod r, logo p-1 tem um grande fator primo, sendo este o r.
Usando o mesmo metodo, p0+2jrs+1 = 0 mod s, pelo que p+1 tem um grande fator primo, o s.
Por ultimo, verificamos pelo algoritmo que r=2it+1, e 2it= 0 mod t, mais uma vez r-1 tem um fator primo t.

Fica entao provado que o nosso algoritmo gera numeros primos fortes.

Para terminar, definimos duas funcoes, que representam respetivamente o algoritmo de Gordon, e o teste de primo forte.


