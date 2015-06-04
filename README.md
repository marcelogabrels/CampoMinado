algoritmo "Campo Minado"
// Função : Réplica funcional do jogo Campo Minado, do Windows.
// Autor : Marcelo Gabriel(35T12), Davi Santana(35T56), Clara Gabrielle(35T56), Fernanda Matias(35T56)
var
   lc,bombasativas:inteiro //LC: A coordenada inserida pelo jogador,bombasativas: número de bombas que restam para serem marcadas
   x,y,i,j:inteiro //X e Y: A coordenada X e Y de LC(separadas),I e J: Contadores para os "Paras"
   derrota,vitoria,mostrarBombas:logico //Flags para indicar um possível término do jogo com seu resultado e determinadas ações para cada um deles.
   mcoordenada:vetor [1..6,1..6] de inteiro //Matriz para armazenamento de dados do jogo
   cm:vetor [1..6,1..6] de literal //Matriz para visualização do jogo
inicio
   vitoria<-falso
   derrota<-falso
   mostrarBombas<-falso
   escreval("####################################################")
   escreval("#####               Campo Minado              ######")
   escreval("####################################################")
   escreval("")
   escreval("-- INSTRUÇÕES --")
   escreval("- Para verificar um bloco, informe a posição no formato lc (linha/coluna), com um número inteiro.")
   escreval("-> Ex: 25 significa linha 2, coluna 5")
   escreval("- Para marcar uma bomba ou desmarcar uma bomba previamente marcada, informe a posição no formato -lc.")
   escreval("-> Ex: -41 significa linha 4, coluna 1.")
   escreval("- Para marcar uma bomba, informe a posição no formato -lc.")
   escreval("")
   para i de 1 ate 6 passo 1 faca //Inicializar campo
      para j de 1 ate 6 passo 1 faca
         mcoordenada[i,j]<--1
      fimpara
   fimpara
   enquanto (vitoria=falso) ou (derrota=falso) faca
      para i de 1 ate 6 passo 1 faca
         para j de 1 ate 6 passo 1 faca //Conversão entre a lógica e memória do jogo para uma representação visual
            escolha (mcoordenada[i,j])
               caso -1
                  cm[i,j]<-("#")
               caso 0
                  cm[i,j]<-("0")
               caso 1
                  cm[i,j]<-("1")
               caso 2
                  cm[i,j]<-("2")
               caso 3
                  cm[i,j]<-("3")
               caso 4
                  cm[i,j]<-("4")
               caso 5
                  cm[i,j]<-("5")
               caso 11 //11 será o código para bomba marcada(ou especifique outro, quem for fazer essa parte.)
                  cm[i,j]<-("*")
               caso 22 //22 será o código para bomba explodida(ou especifique outro, quem for fazer essa parte.)Provavelmente vai ser removida, pois só
                  cm[i,j]<-("X") //se mostra as bombas quando se perde.
            fimescolha
         fimpara
      fimpara
      escreval("     1  2  3  4  5  6")
      escreval("  |-------------------|")
      escreval("1 |  ",cm[1,1],"  ",cm[1,2],"  ",cm[1,3],"  ",cm[1,4],"  ",cm[1,5],"  ",cm[1,6]," |")
      escreval("2 |  ",cm[2,1],"  ",cm[2,2],"  ",cm[2,3],"  ",cm[2,4],"  ",cm[2,5],"  ",cm[2,6]," |")
      escreval("3 |  ",cm[3,1],"  ",cm[3,2],"  ",cm[3,3],"  ",cm[3,4],"  ",cm[3,5],"  ",cm[3,6]," |")
      escreval("4 |  ",cm[4,1],"  ",cm[4,2],"  ",cm[4,3],"  ",cm[4,4],"  ",cm[4,5],"  ",cm[4,6]," |")
      escreval("5 |  ",cm[5,1],"  ",cm[5,2],"  ",cm[5,3],"  ",cm[5,4],"  ",cm[5,5],"  ",cm[5,6]," |")
      escreval("6 |  ",cm[6,1],"  ",cm[6,2],"  ",cm[6,3],"  ",cm[6,4],"  ",cm[6,5],"  ",cm[6,6]," |")
      escreval("  |-------------------|")
      escreva("> Informe a posição XY:")
      leia(lc)
      x<-lc\10
      y<-lc%10
      limpatela
   fimenquanto
   se vitoria entao //Se houve alguma variável que encerrou o jogo, as variáveis de resultado serão analisadas aqui e o resultado obtido, divulgado.
      escreval("8)")
      escreval("Parabéns, você ganhou!")
   senao
      se derrota entao
         escreval("X_X")
         escreval("Você perdeu!")
      fimse
   fimse
fimalgoritmo
