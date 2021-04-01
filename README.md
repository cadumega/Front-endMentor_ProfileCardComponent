![image](https://user-images.githubusercontent.com/72901445/113341407-80cc7500-9303-11eb-825a-93b6d42d747b.png)

1- Baixei os arquivos com as especificações de estilo e do projeto. Contendo arquivos de imagens, read.me , stylereadme.
	Juntar as pastas com as imagens, com os arquivos que irei criar do projeto.

2-  Criando os arquivos de index.html e style.css . Além de referenciar em head a estrutura do html a folha de css.
```
  <link rel="stylesheet" href="style.css">
```

3- Preciso delimitar o container (que é o retangulo da imagem azulado com verde) , cima e baixo tem uma espécie de balão, nos arquivos tem balão top and bottom.
	Crio uma  div para isso na qual irei colocar outras 2 div :
```
  <div class="container">
    
  </div> 
```
	para colocar as 2 imagens..
```
  <div class="container">
    <div class="bg-ballon-top">
      <img src='images/bg-pattern-top.svg' alt="">
    </div>
    <div class="bg-ballon-bottom">
      <img src="images/bg-pattern-bottom.svg" alt="">
    </div>
  </div> 
```

// posso deixar comentado essa parte das imagens, para estar vendo a estruturação do html.

4- Card esta centralizado, fica mais fácil para usar o flexbox do css, prefiro envolver todo o card principal como conteúdo, depois centralizo ele como um todo. Vamos para criação do card principal
```
<div class="content">
      <div class="card">
        
      </div>
    </div>

```

obs: Em alguns momentos, é normal esquecer alguma div , e por conseguinte criar depois para melhorar a estruturação da página. Retornamos ao html para isso, pois com a prática vamos imaginando várias caixinhas para estruturar, algo interessante é quem mexe com bootstrap tem uns cards prontos, tomar como referência o que o bootstrap já montou. Ou dar um f12 para verificar na inspeção os Elements como estruturou.

Dentro do card principal, tenho outros cards.

5- Abracei a imagem com span e não com div, para não deixar solto.
```
<div class="content">
      <div class="card">
        <div class="card-principal">
          <span class="img-profile">
            <img src="images/image-victor.jpg" alt="">
          </span>
        </div>
      </div>
    </div>
```


obs: Poderia fazer de outra forma, utilizando o before no css, e no content colocaria a idade 26, mas imaginando que esse dado venha de servidor ou de outra forma, é melhor tratar direto no html do que no content do css, fica mais difícil de jogar a informação no css.

6- Fechar o meu card profile, adicionei h2 e p
```
    <div class="content">
      <div class="card">
        <div class="card-principal">
          <span class="img-profile">
            <img src="images/image-victor.jpg" alt="">
          </span>
          <h2 class="name-profile">
          Victor Crest
          <span class="age-profile">26</span>
          </h2>
          <p class="city-profile">London</p>
        </div>
      </div>
    </div>
```

6- Sequencia de informações na vertical ou horizontal, imagino como uma lista não ordenada, é igual menu... home inicio sobre serviços contatos... , informações elencadas costumo trabalhar com listas não ordenadas ul

```
<div class="card-footer"></div>
      <ul class="social-numbers">
        li.item-social-numbers*3    //dar tab para habilitar o emmet + rápido para codar
      </ul>
    </div> 
```

cada um desses li são os bloquinhos "followers, likes,photos"
```
<div class="card-footer">
            <ul class="social-numbers">
              <li class="item-social-numbers">
                <span class="number">80k</span>
                <span class="social-description">Followers</span>
              </li>
              <li class="item-social-numbers">
                <span class="number">803k</span>
                <span class="social-description">Likes</span>
              </li>
              <li class="item-social-numbers">
                <span class="number">50</span>
                <span class="social-description">Photos</span>
              </li>
            </ul>
        </div>
```
___
Começar a estilizar o projeto, colorir o projeto. style.css , guia o style-guide.md que foi disponibilizado.
Posso importar para o style.css a fonte ou copiar e colar o link gerado da fonte. Cola na head a família da fonte, iremos setar no body também.

Iremos criar algumas variáveis de css das cores que serão utilizadas várias vezes.
A variável irá guardar a coloração, e iremos usar em cada elemento.
1 rem = 18 px o que coloquei no body,html
Utilizado o sass-lang.com que é um pré processamento de escolha da cor. Mas iremos ver a base de escolha sem ser por esse modo.

1-  elemento root  irá usar para toda documentação
montamos as variáveis com 2 tracinhos e o nome, como é nome composto botei um traço a mais.
```
:root {
  --dark-cyan: hsl(185, 75%, 39%);
  --dark-blue: hsl(229, 23%, 23%);
  --dark-grayish: hsl(227, 10%, 46%);
  --dark-gray: hsl(0, 0%, 59%); 
}
```
2- elemento reset * , limpar tudo que esta pré definido 
reset também no ul, para aplicar o meu comportamento de posicionamento quando estilizar a lista não ordenada

```

* {
  margin: 0;
  padding: 0;
}
ul {
  list-style-type: none;
  margin-block-start: 0;
  margin-block-end: 0;
  margin-inline-start: 0;
  margin-inline-end: 0;
  padding-inline-start: 0;
}
```

3- Começar a estilizar.. Verificando no style guide , a font-family, font-size
```
body {
  font-family: 'Kumbh Sans', sans-serif; 
  font-size: 18px;     
}
```

Irei utilizar a variável css, para puxar a color que setei antes, sem precisar digitar # o código dar cor...
O que abraça o html é o body todo, logo o height 100% joga a cor todo nele body,html. Para o container pegar também.
```
body ,html{
  font-family: 'Kumbh Sans', sans-serif; 
  font-size: 18px;     
  height: 100%;
}
.container {
  background-color: var(--dark-cyan);
  height: 100%; 
}
```

4- Trabalhar com os 2 baloons sobrepondo o background. Uma a esquerda e outra a direita.
position relative , se posiciona conforme os objetos renderizados na tela. Acaba arrastando para baixo o card. Um elemento depois o outro.
position absolute,  ocupada 0 left e top ,subindo o elemento card. Joga um elemento em cima do outro independentemente.
Maior z index, mais a frente, sobrescrever para a maioria dos elementos, bootstrap costuma colocar 99999. Só funciona com o position.

5- CARD
Colocar uma borda para conseguir verificar como esta ficando em relação a div. Bom para rever os posicionamentos das divs com o html. 
Trabalhar a parte central do card.
```
.card {
  border: 1px solid black;
  position: relative;
  z-index: 10;
}
```

Verifiquei que tem um excedente na imagem para fora, não irei utilizar, preciso usar o elemento overflow:hidden, mas preciso posicionar também.
```
.container {
  background-color: var(--dark-cyan);
  height: 100%;
  position: relative; 
  overflow: hidden;
}
```


Deixar bordar arredondada .  border-radius , tamanho foi no olho, já que não tinha no guide-style.
background o padrão é repetir a imagem,
```
.card {
  position: relative;
  z-index: 10;
  width: 325px;
  height: 375px;
  background-color: #fff;
  border-radius: 15px;
  background-image: url('images/bg-pattern-card.svg');
  background-repeat: no-repeat;
}
```

// para escrever menos background. posso colocar a propriedade :
// aplicando display flex, alinho um ao lado do outro , com as outras propriedades.
```
.card {
  position: relative;
  z-index: 10;
  width: 325px;
  height: 375px;
  border-radius: 15px;
  background: #fff url('images/bg-pattern-card.svg') no-repeat;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
```
Centralizar ao centro
```
.content{
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

Usar a propriedade display, para centralizar todo o conteúdo do card-profile, text align seria só o texto.
```
.card-profile {
  display: flex;
  flex-direction: column;
  align-items: center;
}
```

Arredondar imagem
```
.img-profile img {
  max-width: 100%;
  border-radius: 50%;
  border: 5px solid #fff;
}
```

Textos name abaixo da imagem circular , capitalize para primeira letras maisculas
```
.name-profile {
  text-transform: capitalize;
  font-size: 17px;
  font-weight: 700;
  color: var(--dark-blue);
  padding-top: 1rem;
}
```

Estilizações
```
.age-profile {
  color: var(--dark-grayish);
  font-weight: 400;
}
.city-profile {
  text-transform: capitalize;
  color: var(--dark-gray);
  font-size: 14px;
  padding-top: .5rem;
  margin-bottom: 2rem;
  text-align: center;
}
```

// bottom: 0; é onde segura mais abaixo, com position absolute, se for relative iria mais abaixo
div renderiza em bloco, um embaixo do outro, span não.

```
.card-footer {
  position: absolute;
  bottom: 0;
  border-top: 1px solid #e9e9e9;
  width: 100%;
}
.social-numbers {
  display: flex;
  justify-content: space-around;
  font-size: 14px;
}
.item-social-numbers {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 1.5rem;
  margin-bottom: 1.5rem;
}
.number {
  font-weight: 700;
  font-size: 20px;
  margin-bottom: .2rem ;
}
.social-description {
  text-transform: capitalize;
  font-size: 10px;
  font-weight: 300;
  letter-spacing: 2px;
}
```
