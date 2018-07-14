
<img src="logo.png" style="float:right">


# Sumário

<!-- TOC -->

- [Sumário](#sumário)
- [Sobre este curso](#sobre-este-curso)
- [E a documentação oficial?](#e-a-documentação-oficial)
- [Porque existe a separação entre frontend e backend?](#porque-existe-a-separação-entre-frontend-e-backend)
- [O que é Vue.js?](#o-que-é-vuejs)
- [E o backend?](#e-o-backend)
- [Preparando o ambiente](#preparando-o-ambiente)
    - [Conhecendo o Node, npx e npm](#conhecendo-o-node-npx-e-npm)
    - [Instalando e Configurando o Visual Studio Code](#instalando-e-configurando-o-visual-studio-code)
    - [Instlalando o Vue através do vue-cli](#instlalando-o-vue-através-do-vue-cli)
- [Criando o projeto Vue](#criando-o-projeto-vue)
- [Comentários](#comentários)

<!-- /TOC -->

# Sobre este curso

Este mini curso tem como objetivo introduzir o Framework Javascript Vue.js para o desenvolvimento de aplicações que chamamos de SPA - *Single Page Applications*, isto é, aplicações de página única. Este conceito é o inverso dos sistemas Web mais comuns onde cada funcionalidade é uma página ou uma requisição que contém uma página completa. No desenvolvimento atual, existe uma separação muito clara entre frontend e backend, e o Vue.js entra no papel de framework frontend.

# E a documentação oficial?

A [documentação oficial](https://br.vuejs.org/v2/guide/) que inclusive está em português pode ser lida antes desse curso. Lá você você verá diversas funcionalidades do Vue, só que funcionando em modo desconexo. Vários exemplos da documentação oficial usam o Vue  através da sua própria instância, como por exemplo:

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Olá Vue!'
  }
})
```

O que pode ser confuso para quem está iniciando, e deseja ver um exemplo real em funcionamento. A minha dica é, use a documentação oficial para resolver pequenas dúvidas ou reler alguns dos conceitos do Vue.

Este mini curso visa suprir essa deficiência da documentação oficial, no qual queremos ver um exemplo real em funcionamento.

# Porque existe a separação entre frontend e backend?

O desenvolvimento de sistemas vem passando ao longo dos últimos anos uma mudança significativa, motivada principalmente pela entrada dos dispositivos mobile como principal meio de uso e acesso aos sistemas. Antigamente, um sistema poderia ser 100% web e estaria atendendo aos requisitos básicos do cliente, mas hoje em dia o sistema deve ser capaz de ser web e mobile, independente do tipo de dispositivo mobile. 

A comunicação entre *frontend* e *backend* é realizada através de [RESTfull](https://pt.wikipedia.org/wiki/REST). Basicamente, o *frontend* acessa o *backend* via ajax, e o *backend* responde com algum dado no formato Json.


# O que é Vue.js?

O Vue (a mesma pronúncia de *view* no inglês, isto é, *víu*) é um framework javascript que "cuida" de toda a parte do desenvolvimento *frontend*. Através dele será possível criar todas as telas de um sistema, contendo formulários, campos, tabelas, abas, etc. Além disso, existem diversas bibliotecas para o Vue que maximizam as suas funcionalidades. O Vue é um concorrente direto de outros dois frameworks, Angular e React. Estes 3 frameworks hoje em dia estão entre os prediletos para o desenvolvimento *frontend*.

O Vue exige um pouco de conhecimento em HTML, JavaScript e CSS, que são as três bases do desenvolvimento web, mas não é obrigatório que você seja um expert para poder continuar o curso. Será um "passeio no parque" se você já conhece bem Javascript e está familiarizado com ES2016. 

Se você começar a estudar o Vue pela [documentação oficial](https://br.vuejs.org/v2/guide/index.html) (que aliás é ótima, e em português), verá coisas do tipo:

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

Nosso curso aborda o Vue de uma forma diferente da documentação oficial, de forma a prepará-lo para o "mundo real", usando o que há de melhor no framework. Isso significa que, quando começarmos a aprender Vue, estaremos usando um *template* pronto com vários arquivos prontos, tudo funcionando de forma sincronizada para que se possa obter o máximo de proveito do Vue. Para chegarmos nesse ponto, precisamos primeiro preparar o nosso ambiente de desenvolvimento.

# E o backend?

Nesse mini curso estaremos usando um backend genérico que eu mesmo criei e está localizado em [http://northwind.now.sh/](http://northwind.now.sh/). Neste back poderemos fazer operações Rest, das quais destacamos:

| Método | URI | Entrada | Saída |
|--------|-----|---------|-------|
| GET | /api/categories | void | Array contendo todas as categorias |
| GET | /api/categories/:id | id | Uma categoria |

<!--TODO continuar os métodos --> 

# Preparando o ambiente

O Vue precisa de muito pouco para que possamos iniciar o seu estudo:

- **Git** Imprescindível no desenvolvimento de hoje, o [Git](https://git-scm.com/) é usado para manter o controle de versão dos arquivos. Ele não é um requisito para que o Vue funcione, mas é uma ótima ideia ter o Git instalado e poder versionar os seus arquivos de projeto.

- **Node** Acesse [https://nodejs.org/en/](https://nodejs.org/en/) e instale o Node versão 8 ou superior. Para ambientes Linux baseado no Debian, pode-se fazer `sudo apt-get install nodejs`, mas tenha certeza que está na versão 8! Para saber a versçao do node, execute `node -v` no terminal.

- **Visual Studio Code** Esta é definitivamente a melhor IDE gratuita para o desenvolvimento Vue. O "VSCode" vem se destacando no mercado no desenvolvimento html/javascript/css e, com a devida configuração, é perfeitamente compatível com o Vue. 

## Conhecendo o Node, npx e npm

Após instalar o Node em seu ambiente, podemos executá-lo através da linha de comando. Basta digitar `node` e entrar no modo interativo. Mas para nós desenvolvedores, o Node possui uma ferramenta muito útil chamada `npm`, que é o gerenciador de pacotes do node.

O npm funciona da seguinte forma:

```bash
npm install <nomedabibliioteca> --save
```

A diretiva `--save` faz com que a biblioteca seja "salva" no projeto em que estamos trabalhando. Essas informações são salvas no arquivo `package.json`, no qual o examinaremos melhor assim que criarmos um projeto Vue. 

## Instalando e Configurando o Visual Studio Code

Instale o [VSCode](https://code.visualstudio.com/) e, após a instalação, navegue até a aba de extensões:

<p align="center">
<img src="https://i.imgur.com/POtr81y.png">
</p>

Ao clicar nesta aba, você poderá procurar e instalar centenas de extensões para customizar o seu VSCode. No nosso caso, estaremos instalando as extensões para que o Vue seja reconhecido pela ide. As extensões que você deve instalar são:

- Editorconfig
- ESLInt
- vue
- vetur
- vue peek
- vue 2 Snippets  

Após instalar todas estas extensões, reinicie o VSCode. 

## Instlalando o Vue através do vue-cli

O vue-cli é a melhor forma de criar um projeto base totalmente funcional. Para instalar o vue-cli, faça:

```bash
$ npm install -g @vue/cli
```

A diretiva `-g` irá configurar o *vue-cli* como global, assim você pode usar o comando em qualquer diretório. 

# Criando o projeto Vue

Com o terminal aberto, pode-se crie o projeto vue da seguinte forma:

```bash
& vue create myapp
```

Após digitar este comando, surge a pergunta do tipo de projeto que queremos criar. Vamos escolher "Manually select features" para escolher as bibliotecas mais importantes:

<p align="center">
<img src="https://i.imgur.com/HumiAOK.png">
</p>

Das bibliotecas disponíveis, vamos selecionar: Babel, Router e Linter, conforme a figura a seguir:

<p align="center">
<img src="https://i.imgur.com/cqvhV42.png">
</p>

Para todas as outras opções, deixe a padrão. O projeto é criado, e já podemos abrí-lo no VSCode da seguinte forma:

```bash
$ cd myapp
$ code .
```








# Comentários

O curso ainda está no começo, mas você pode dizer aí em baixo o que gostaria de ver nele! A ideia básica é detalhar toda a construção da aplicação https://vuewind.now.sh/

<div id="disqus_thread"></div>
<script>
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://danielschmitz.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>