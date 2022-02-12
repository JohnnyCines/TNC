O objetivo da assinatura digital RSA é a troca de informacao, de forma a que o destinatario consiga verificar o remetente, e que esta informacao nao tenha sido alterada.

Comecamos por gerar o conjunto de chaves privada e publica para o sistema de cifracao RSA como vimos ao longo das aulas.

Para possibilitar o envio que qualquer tipo de informacao, seja um ficheiro de texto, ou um pdf. Aplicamos a funcao de hash, sha256, predefinida na biblioteca hashlib. O que produz uma mensagem de comprimento 256 bits independentemente do tipo ou tamanho da informacao original, o que em casos raros, podera resultar em mensagem diferentes terem o mesmo valor hash.

Para assinar a nossa mensagem, computamos o resultado de m^d mod n, sendo d a chave privada RSA, o n uma parte da chave publica, e m a nossa mensagem apos a aplicacao do hash.

Agora que a mensagem esta assinada, enviamos a mensagem original, e a sua assinatura para o destinatario.
Este para verificar a informacao comeca por novamente a funcao de hash a mensagem.

Seguidamente, para reverter o processo de assinatura, calcula  s^e mod n, sendo (e, n) a chave publica do remente, e s a assinatura recebida.
Podemos agora comparar o resultado do hash da mensagem, e a reversao da assinatura. Caso estes dois valores sejam identicos, podemos afirmar que foi autor desta chave que enviou a mensagem, e a mesma nao foi alterada posteriormente.

A diferença entre a assinatura RSA e a assinatura cega RSA(ou de Chaum), é que na assinatura de Chaum não será o autor da mensagem a realizar a assinatura e a entidade que realiza a assinatura não irá ter acesso a mensagem original.

Começamos por ofuscar a mensagem original, para tal usando a chave publica RSA do assinante, será gerada uma chave k que pertence ao sistem reduzido de residuos base n, seguidamente utilizando k computamos o resultado de m*k^e mod n, esta será a mensagem a ser assinada.

Na fase de assinatura, utilizando a mensagem previamente calculada,m', e a chave privada, d, computamos m^d mod n e devolvendo o resultado, s', ao autor da mensagem original. 

Este será capaz de reverter a ofuscação inicialmente realizada multiplicando o inverso de k por s', e este resultado sera a mensagem original assinada por um terceira entidade.

Começamos por aplicar o hash para possibilitar o envio de qualquer tipo de informação

...
explicar funções
...