# Descrição do projeto

O objetivo do projeto é modelar uma ultra simplificação do jogo “Monopoly” através de uma cadeia de Markov. Mais especificamente, considere o seguinte conjunto de regras:

- O tabuleiro consiste em $40$ casas, dispostas circularmente, enumeradas de $0$ até $39$. Após a casa $39$, retorna-se à casa $0$.
- O jogador começa na casa de número $0$, e o número de casas que ele irá andar, sempre no sentido crescente, é a soma do resultado obtido em dois lançamentos de um dado honesto de $6$ faces.
- A casa de número $20$ é uma casa especial, denominada “prisão”. Caso o jogador caia em tal casa através da rolagem de dados, o jogo segue normalmente (chamamos esse caso de “visita à prisão”). Porém o jogador pode ir preso se, a qualquer momento do jogo, nas rolagens dos dados ele obtiver uma sequência de três lançamentos com valores repetidos (chamemos esse caso de “ir preso”). Vejamos em exemplos:
    - Se o jogador está na casa de número $15$ e obtém $2 + 3$ na rolagem dos dados, ele irá somente visitar a prisão e seguirá jogando normalmente daí em diante.
    - Se o jogador está na casa de número $7$, e obtém $4 + 4$ na rolagem dos dados, ele deverá lançá-los novamente. Caso obtenha valores distintos na nova rolagem, digamos $4 + 6$, ele irá para a casa de número $17$ e o jogo segue normalmente. Mas caso obtenha valores iguais na nova rolagem, digamos $5 + 5$, uma nova rolagem deverá ser feita. Se nessa nova rolagem valores distintos forem observados, segue o jogo, mas se valores iguais forem observados uma terceira vez, o jogador irá automaticamente para a prisão.
- O jogador fica no máximo três rodadas na prisão, mas pode sair antes se obtiver valores repetidos no lançamento dos dados. Por exemplo:
    - Imediatamente ao ir preso, o jogador lança o par de dados. Se ele obtiver valores iguais, digamos $2 + 2$, ele está imediatamente solto e lança o par de dados novamente para saber para qual casa ele irá, partindo da casa $20$. Se ele obtiver valores diferentes, digamos $2 + 5$, ele lança novamente o par de dados: obtendo valores iguais está solto e obtendo valores diferentes continua preso. Neste ́último caso, ele passa mais uma rodada na prisão e em seguida ́é automaticamente solto, seguindo o jogo normalmente.
- O jogador fica caminhando no tabuleiro indefinidamente de acordo com tais regras.

Com base nisso, faça o que se pede abaixo:

1. Explique como que o cenário acima descrito pode ser modelado por uma cadeia de Markov, descrevendo detalhadamente os estados de sua cadeia e exibindo a sua matriz de probabilidades de transição. Cada passo de sua construção deve ser descrito de forma detalhada.
2. Denote por $(X_t)_{t \in \mathbb{Z} \ge 0}$  a posição do jogador no tabuleiro ao longo do tempo. Pelo item 1), sabemos que essa sequência de variáveis aleatórias ́é descrita por uma cadeia de Markov. Construa um algoritmo para simular observações de tal cadeia, onde ́é possível controlar o número de iterações desejadas.
3. Seja $Y$ a variável aleatória que representa a quantidade de passos que o jogador dá até a sua primeira prisão (tome cuidado, não é a primeira “visita a prisão”!). Obtenha uma aproximação para o valor esperado de $Y$, através de sucessivas simulações da cadeia usando o algoritmo construído no item 2). Descreva detalhadamente o seu procedimento para realizar tal aproximação.
4. Justifique matematicamente porque o procedimento realizado no item 3) funciona para aproximar o valor esperado de $Y$.
5. Seja $Z$ a variável aleatória que representa a posição do jogador no tabuleiro após transcorrido um tempo suficientemente longo, ou seja, $X_t$ quando $t\to\infty$. Encontre a função massa de probabilidade de $Z$. Em média, em qual casa o jogador passa mais tempo? Discuta os resultados obtidos.
