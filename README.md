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
          <span class="age=profile" 26></span>
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
          <li class="item-social-numbers"></li>
            <span class="number">80k</span>
            <span class="social-description">Followers</span>
          <li class="item-social-numbers"></li>
            <span class="number">803k</span>
            <span class="social-description">Likes</span>
          <li class="item-social-numbers"></li>
            <span class="number">50</span>
            <span class="social-description">Photos</span>
        </ul>
      </div>
```
___
Começar a estilizar o projeto, colorir o projeto. style.css , guia o style-guide.md que foi disponibilizado.
Posso importar para o style.css a fonte ou copiar e colar o link gerado da fonte. Cola na head a família da fonte, iremos setar no body também.

Iremos criar algumas variáveis de css das cores que serão utilizadas várias vezes.
A variável irá guardar a coloração, e iremos usar em cada elemento.
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
position relative , se posiciona conforme os objetos renderizados na tela. Acaba arrastando para baixo o card.
position absolute,  ocupada 0 left e top ,subindo o elemento card.
Maior z index, mais a frente, sobrescrever para a maioria dos elementos, bootstrap costuma colocar 99999.