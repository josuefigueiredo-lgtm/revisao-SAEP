Documentação: Corrida da Revisão SAEP
Visão geral

Jogo de perguntas e respostas para revisão em sala, jogado por equipes que se alternam na mesma tela (por exemplo, no projetor). É um único arquivo HTML, com CSS e JavaScript puros, sem bibliotecas e sem servidor. Funciona offline e se adapta ao modo claro ou escuro do dispositivo.

Como jogar
Na tela inicial, edite os nomes das equipes. Use + Adicionar equipe e Remover última (de 2 a 8 equipes).
Defina o total de perguntas (padrão 20, máximo 69). Ele é dividido igualmente entre as equipes, e a tela mostra o cálculo.
Clique em Começar o jogo. A Equipe 1 abre, e a vez passa para a próxima equipe a cada pergunta, acertando ou não.
Cada pergunta tem 30 segundos. Ao responder (ou quando o tempo acaba), o jogo mostra a alternativa correta, o comentário e o código do item de origem.
No fim, aparece o vencedor, ou o empate entre as equipes com a mesma pontuação. O botão Jogar de novo mantém os nomes das equipes e o total escolhido.
Regras de pontuação
Acerto vale 10 pontos mais um bônus de tempo: metade dos segundos restantes, arredondada para cima. A pontuação máxima por pergunta é 25.
Erro ou tempo esgotado vale 0.
Se o total não divide certinho, o jogo arredonda para baixo, para que todas as equipes respondam o mesmo número de vezes. Há no mínimo uma pergunta por equipe.
As perguntas são sorteadas sem repetição dentro de uma partida, e a ordem das alternativas é embaralhada a cada vez.
Estrutura do código
Banco de questões: a constante Q, no início do script. Cada item tem:
t: tema (Requisitos, Metodologias, UML, Programação e dados, IoT e implantação);
id: código do item da prova;
q: enunciado;
o: lista de alternativas;
a: posição da alternativa correta, começando em 0;
e: comentário mostrado após a resposta.
Estado do jogo: list (perguntas da partida), i (pergunta atual), sc (pontuações), turn (equipe da vez), left (tempo restante), tm (cronômetro), names (nomes na partida), tn (nomes digitados) e tot (total de perguntas).
Funções:
el e shuf são auxiliares para criar elementos e embaralhar;
start desenha a tela inicial;
board desenha o placar;
show desenha a pergunta e controla o tempo e a resposta;
end mostra o resultado.
Estilo: as cores ficam em variáveis CSS no :root, com versão para modo escuro.
Como personalizar
Adicionar questões: inclua novos objetos no final da lista Q, com o mesmo formato. O limite do campo de total acompanha o tamanho da lista.
Mudar o tempo: altere o 30 em três lugares: left=30, left/30*100 e o texto “(30 segundos por pergunta)”.
Mudar a pontuação: ajuste a expressão 10+Math.ceil(left/2) dentro da função reveal.
Mudar o limite de equipes: altere o 8 em tn.length>=8.
Mudar o total padrão: altere tot=20 na declaração das variáveis.
Mudar as cores: edite as variáveis do :root.
Limitações
Não há persistência: fechar ou recarregar a página zera a partida.
É um jogo para uma única tela. Não há login, modo online nem controle de quem clica.
Não há pausa nem sons.
O jogo não impede que a equipe errada clique, então o professor precisa conduzir quem responde.
