# Jogo-Freeway
Aprendizado sobre Java Script - Curso Alura

## Funcionalidade
- Jogo Single Player - Uma pessoa.
- Controles:
| Controle | Jogador  1 |
| ------------- | ------------- |
| Para cima  | " ↑ " |
| Para baixo  | " ↓ " |
- Placar para contar os pontos.

## Sobre Desenvolvimento
- Desenvolvido em Java Script, HTML e CSS no Sketch.
- Variaveis e Funções do Ator, Carros e Placar.
- Utilização de um arquivo puxado de p5.collide2D para funcionalidade de colisão dos carros:
```
function verificaColisao(){
  for (let i = 0; i < imagemCarros.length; i = i + 1){
    colisao = collideRectCircle(xCarros[i], yCarros[i], comprimentoCarro, alturaCarro, xAtor, yAtor, 15);
    if(colisao){
      voltaAtorParaInicial();
      somDaColisao.play();
      if(pontosMaiorQueZero()){
        meusPontos -= 1;
      }
    }
  }
}
```
- Funções para Sons e Imagens do Jogo:
Criamos a variavel e criação uma função "preload" onde atribuimos os caminhos dos arquivos de som e imagem, depois podemos associar onde quisermos no codigo.
```
//codigo imagens/sons

let imagemDaEstrada;
let imagemDoAtor;
let imagemDoCarro1;
let imagemDoCarro2;
let imagemDoCarro3;

let somDaTrilha;
let somDaColisao;
let somDoPonto;

function preload(){
  imagemDaEstrada = loadImage("imagens/estrada.png");
  imagemDoAtor = loadImage("imagens/ator-1.png");
  imagemDoCarro1 = loadImage("imagens/carro-1.png");
  imagemDoCarro2 = loadImage("imagens/carro-2.png");
  imagemDoCarro3 = loadImage("imagens/carro-3.png");
  imagemCarros = [imagemDoCarro1, imagemDoCarro2, imagemDoCarro3, imagemDoCarro1, imagemDoCarro2, imagemDoCarro3];
  
  somDaTrilha = loadSound("sons/trilha.mp3");
  somDaColisao = loadSound("sons/colidiu.mp3");
  somDoPonto = loadSound("sons/pontos.wav");
}
```
- Funções de criação do Sketch.
A função "Draw()" vai executar tudo relacionado ao que você criar.
```
function setup() {
  createCanvas(500, 400);
  somDaTrilha.loop();
}

function draw() {
  background(imagemDaEstrada);
  mostraAtor();
  mostraCarro();
  movimentaCarro();
  movimentaAtor();
  voltaPosicaoInicialDoCarro();
  verificaColisao();
  incluiPontos();
  marcaPontos();
}
```

