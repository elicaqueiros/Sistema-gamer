# Sistema-gamer
atividade final de JS
Élica Queirós Santos Dutra

Código:

const prompt = require("prompt-sync")();


let time = [];


let continuar = true;


function mostrarmenu() {
 console.log("\n========================================");
 console.log("------------SISTEMA GAMER---------------");
 console.log("1 - cadastrar");
 console.log("2 - deletar");
 console.log("3 - mostrar equipe");
 console.log("4 - calcular media da equipe");
 console.log("5 - buscar jogador");
 console.log("6 - Atualizar pontos");
 console.log("7 - sair");
 console.log("========================================");
 console.log("\n");
}


function mostraEquipe() {
    if(time.length === 0) {
        return;
    }


    for(let i = 0; i < time.length; i++) {
        let jogador = time[i];
        console.log((i + 1) + ". " + jogador.nome + " | Função: " + jogador.funcao + " | Pontuação: " + jogador.pontuacao);
    }
}


function cadastrarJogador() {
    let nomeJogador = prompt("Digite o nome do jogador: ");
    let funcaoJogador = prompt("Digite a função no time: ");
    let pontuacaoJogador = Number(prompt(" Digite a pontuação: "));
   
    if(isNaN(pontuacaoJogador)) {
        console.log("Pontuação inválida.")
        return;
    } else {
        let recruta = {
            nome: nomeJogador,
            funcao: funcaoJogador,
            pontuacao: pontuacaoJogador,
        }
        time.push(recruta);
        console.log("Jogador " + nomeJogador + " foi cadastrado com sucesso!");
        console.log("-----------------------");
    }
}


function deletarJogador() {
 if (time.length === 0) {
        console.log("Nenhum jogador cadastrado.");
        return;
    }
        let nomeDeletado = prompt("Digite o nome a ser deletado: ");
        let indexDeletado = -1;


        for (let i = 0; i<time.length; i++) {


            if (time[i].nome === nomeDeletado) {
                indexDeletado = i;
                break;
            }
        }
       
    let index = time.indexOf(nomeDeletado);


    if (indexDeletado === -1) {
        console.log("Jogador não encontrado.");
        return;
    }


    time.splice(index, 1);
    console.log("Jogador deletado com sucesso.");


}


function calculoDaMedia() {
    if (time.length === 0) {
        console.log("Nenhum jogador cadastrado.");
        return;
    }


    let totalPontos = 0;


    for (let i = 0; i < time.length; i++) {
        totalPontos = totalPontos + time[i].pontuacao;
    }


    let mediaPontos = totalPontos / time.length;


    console.log("O time possuí uma pontuação média de: ", mediaPontos);
}




function buscarjogador(nomedesejado) {
 console.log("buscando por: " + nomedesejado + "...");
 let encontrou = false;
 for (let i = 0; i < time.length; i++) {
 let jogadoratual = time[i];


 if (jogadoratual.nome === nomedesejado) {
 console.log("JOGADOR ENCONTRADO!");
 console.log("Nome: " + jogadoratual.nome + " | pontos : " + jogadoratual.pontuacao)
 encontrou = true;
 break;
 }


 }
 if (encontrou === false) {
 console.log("O jogador " + nomedesejado + " não faz parte da nossa equipe.")
 }
 }


function atualizarPontuacao() {
  if (time.length === 0) {
    console.log("Nenhum jogador cadastrado.");
    return;
  }


  console.log("\n--- ATUALIZAÇÃO DE RANKING ---");
  let nomeProcurado = prompt("Qual jogador deseja atualizar? ");
  let jogadorEncontrado = false;


  // Percorre a lista com o loop for tradicional
  for (let i = 0; i < time.length; i++) {
    if (time[i].nome === nomeProcurado) {
      jogadorEncontrado = true;


      let pontosNovos = Number(prompt("Quantos pontos ele ganhou hoje? "));


      if (isNaN(pontosNovos) || pontosNovos < 0) {
        console.log("Pontuação inválida!");
        return;
      }


      // Soma a pontuação atual com os novos pontos
      time[i].pontuacao += pontosNovos;


      console.log(`SUCESSO! A pontuação de ${time[i].nome} subiu para ${time[i].pontuacao} pontos!`);
      break; // Interrompe o loop ao encontrar e atualizar
    }
  }


  // Se o loop terminou e não encontrou ninguém
  if (!jogadorEncontrado) {
    console.log("Jogador não encontrado.");
  }
}


 while(continuar === true) {
 mostrarmenu();
 let opcao = prompt("digite sua opção: ");


 if (opcao === "1") {
 cadastrarjogador();
 } else if (opcao === "2") {
 deletarjogador();
 } else if (opcao === "3") {
 mostraequipe();
 } else if (opcao === "4") {
 calculodamedia();
 } else if (opcao === "5") {
 let nome = prompt("Digite o nome do jogador: ");
 buscarjogador(nome);
 } else if (opcao === "6") {
 atualizarpontuacao();


 }else if (opcao === "7") {
 continuar = false;
 } else {


sistema-gamer.js
 console.log("Opção invalida, digite outra opção")
 }
 }



