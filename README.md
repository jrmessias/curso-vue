
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
    - [Instlalando o vue-cli](#instlalando-o-vue-cli)
- [Criando o projeto Vue](#criando-o-projeto-vue)
- [Conhecendo os arquivos principais do projeto](#conhecendo-os-arquivos-principais-do-projeto)
- [Executando o seu projeto no modo "dev"](#executando-o-seu-projeto-no-modo-dev)
- [Compreendendo melhor o router](#compreendendo-melhor-o-router)
- [Preparando o acesso ao backend](#preparando-o-acesso-ao-backend)
    - [Instalando o Axios](#instalando-o-axios)
    - [Utilizando o Axios](#utilizando-o-axios)
- [Criando o service *categories* para acesso ao servidor](#criando-o-service-categories-para-acesso-ao-servidor)
    - [Testando o service de categorias](#testando-o-service-de-categorias)
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

Para melhorar a integração do VScode com o Vue, abra as configurações do VSCode (Arquivo > Preferências > Confgurações ) e adicione a seguinte configuração:

```json
{
  "vetur.format.defaultFormatter.js": "vscode-typescript",
  "vetur.format.defaultFormatter.html": "js-beautify-html",
  "javascript.format.insertSpaceBeforeFunctionParenthesis": true,
  "eslint.autoFixOnSave": true,
  "eslint.validate": [
    {
      "language": "vue",
      "autoFix": true
    },
    {
      "language": "html",
      "autoFix": true
    },
    {
      "language": "javascript",
      "autoFix": true
    }
  ]
}
```

## Instlalando o vue-cli

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

Com o VSCode aberto, temos algo parecido com:

<p align="center">
<img src="https://i.imgur.com/ycCvofh.png">
</p>

# Conhecendo os arquivos principais do projeto

A seguir vamos comentar alguns arquivos que fazem parte do projeto.

**package.json** Contém as configurações do projeto, como o seu nome, versão, os pacotes node que estão instalados e as rotinas para serem executadas quando você deseja, por exemplo, compilar (build) o seu projeto.

**src/main.js** Podemos considerar este o arquivo inicial do projeto, o que configura o Vue e algumas bibliotecas. Se você abrí-lo no VSCode, verá que ele "carrega" o arquivo `App.vue`.

**src/App.vue** Este é o primeiro componente Vue a ser carregado. Ele pode ser compreendido como toda a aplicação Vue na tela, sendo que demais componentes serão carregados "dentro" do App.vue. Veremos mais detalhes sobre isso.

**src/router.js** Define as rotas da aplicação, isto é, quando mudamos a url do navegador qual componente deve ser carregado. Na aplicação recém criada temos a url "/" que carrega o componente `Home`, e a url `/about` que carrega o componente `About`.

**src/views/About.vue** As "views" são componentes que o router carrega e adiciona na aplicação. Você pode pensar na view como uma página, onde cada página é carregada pelo router. 

**src/components/homeworld.vue** Um componente pode ser definido como algo visual que será reaproveitado em diversas partes do seu projeto. Suponha que você crie um componente de upload de arquivos, e deseja usá-lo em 3 lugares diferentes. Então você deve criar este componente no diretório `components`. Neste mini curso não iremos focar muito na criação de componentes, apenas na criação de views.

# Executando o seu projeto no modo "dev"

Para executar o projeto Vue, faça o seguinte comando no terminal:

```bash
$ npm run serve
```

O projeto será compilado, e terá como resposta algo como:

<p align="center">
<img src="https://i.imgur.com/FcqiMjC.png">
</p>

Acesse http://localhost:8080/#/ para ver o Vue em ação. Você verá algo como:

<p align="center">
<img src="https://i.imgur.com/GqI2vXr.png">
</p>

Como teste, abra o arquivo `src/views/Home.vue` e altere a mensagem de boas vindas para "Bem vindo a sua aplicação Vue". Quando salvar o arquivo, verá que a aplicação foi recompilada e a página no navegador atualizada.

# Compreendendo melhor o router

O principal objetivo do router no Vue é carregar os componentes na tela de acordo com uma rota estabelecida. Para conhecer melhor o router, você precisa saber onde ficam 3 funcionalidades básicas:

- **Onde o router é configurado?** Ele fica especificamente no `src/router.js`. Lá você encontrará duas rotas. A primeira, usa o caminho "/" e aponta para o componente `Home`. Isso é, quando a url for "/", carregue o componente "Home". A segunda rota usa o caminho `/about` e liga ao componente "About". Criar novas rotas é criar mais uma entrada nessa lista, relacionando o caminho e o componente.

- **Onde o componente é carregado?** Os componentes tem que ser carregdos em algum lugar, nao é mesmo? Para isso usamos a tag `<router-view/>`, e ela está especificamente no `App.vue`. Neste componente, você verá o menu e logo abaixo a tag que define o local onde os componentes são carregados

- **Como eu "chamo" uma rota/componente?** A resposta está no próprio arquivo `App.vue`, onde você tem a tag `router-link` com o atributo "to". Ao clicar nesse link, o router pega o caminho especificado, procura em sua lista de rotas, e carrega o componente no `router-view`.

# Preparando o acesso ao backend

Uma das primeiras tarefas a serem realizadas após a instalação do projeto Vue é preparar o acesso do framework ao backend. Existem centenas de formas de se fazer isso, vou utilizar uma que está presente em quase todos os meus projetos. Quando eu penso em "acesso do frontend ao backend" gosto de pensar como um "service", um conjuto de classes que proveem acesso ao servidor.

Todos estes serviços podem estar no diretório `src/services` que iremos criar. Lembre-se que, pensou em acesso ao backend, o código para isso está no "services". 

## Instalando o Axios

Uma consulta do frontend ao backend pode ser realizado através da biblioteca `axios`, que está disponível para uso em qualquer tipo de ambiente javascript. Nossa primeira tarefa é instalar esta biblioteca:

```bash
$ npm install axios --save
```

Após a instalação, vamos criar o arquivo `src/services/http.js` que será o arquivo responsável em realizar uma configuração inicial na biblioteca, veja:

```js
import axios from 'axios';

const http = axios.create({
  baseURL: "https://northwind.now.sh/api",
  timeout: 10000,
  headers: { 'Content-Type': 'application/json' },
});

export default http;
```

Existem muitos detalhes neste arquivo que estão relacionados ao Javascript em si, não ao Vue. A seguir vamos comentar algumas partes:

- Em `import axios from 'axios'`, importamos a biblioteca "axios" diretamente do diretório `node_modules`. O compilador vai ser inteligente o suficiente para saber procurar a bibliota neste diretório.

- Criamos a constante `http`, e ela é uma instância direta da biblioteca axios. O método `create` é usado para que possamos informar alguns parâmetros extras. Se você conhece o pattern Factory, vai se identificar aqui.

- Os parâmetros, a princípio, são apenas 3. O `baseURL` é o mais importante, ele "aponta" para a url do nosso servidor backend (se você sentiu falta do uso de enviroments aqui, releve. Esse é um curso de principiantes). O parâmetro `timeout` fala por si só, e o parâmetro `headers` está relacionado ao cabeçalho da requisição `http` que será feita ao backend. Neste caso, estaremos sempre repassando o parâmetro `Content-Type` com o valor `application/json`. Aqui usamos Json que será a nossa forma de comunicação padrão.

- Finalmente temos o uso do `export default http`. Essa assinatura exporta a constante `http` para ser utilizada em outros arquivos javascript.

## Utilizando o Axios

Após configurar o Axios, ou seja, criar a classe `http.js` no diretório `src/services`, podemos criar uma classe que será responsável em acessar as informações sobre "categorias". O que vamos fazer, basciamente, é criar um service chamado "categories" com as seguintes funcionalidades:

| Método | URI | Entrada | Saída |
|--------|-----|---------|-------|
| GET | /api/categories | void | Array contendo todas as categorias |
| GET | /api/categories/:id | id | Uma categoria |

# Criando o service *categories* para acesso ao servidor

Crie o arquivo `categories.js` no diretório `src/services`, com o seguinte conteúdo:

```js
import http from './http';

const categories = {
    getAll: () => http.get('/categories'),
    getOne: id => http.get(`/categories/${id}`)
};

export default categories;
```

Na primeira linha temos o import do `http`, que acabamos de criar. O uso do `./` indica o mesmo diretório onde está o arquivo principal.  A partir desse momento não precisamos mais importar o Axios, já que o `http` faz isso. A constante `categories` possui duas propriedades, que na verdade são métodos. 

O primeiro método se chama `getAll` e usa a especificação ECMAScript 2015 chamada de arrow function. Se você nunca viu isso, pode imaginar que `() => http.get('/categories')` é o mesmo que `function() { return http.get('/categories') }`. Fica a dica para estudar um pouco mais sobre essa especificação, pois a veremos muito em todo o código.

Ainda neste primeiro método, temos `http.get` que irá realizar uma requisição http ao endereço repassado. O responsável em gerenciar esse processo é o Axios.

O segundo método, `getOne`, faz o mesmo que o primeiro, só que repassamos o id da categoria.

## Testando o service de categorias

Chegou o momento de ver algo funcionando. Vamos até o arquivo `src/components/HelloWorld.vue` e alterá-lo um pouco para exibir a lista de categorias.

Primeiro, limpe quase todas as informações não pertinentes:

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>
```

Agora, importe o service na tag `<script>`, mas antes do export defualt:

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
import  categories from '../services/categories';
export default {
  name: "HelloWorld",
  props: {
    msg: String
  }
};
</script>
```

Perceba que estamos importando `categories` através de um caminho absoluto. Ou seja, se estamos no diretorio `components`, temos que subir um nível e acessar o diretório `services`. Para facilitar esse processo, pode-se utilizar um alias já criado pelo Vue chamado "@", que aponta diretamente para o diretório `src`. Então, a chamada ao service pode ser:  `import categories from '@/services/categories';`

Após importar o `categories`, vamos usá-lo no método `mounted`, que é executado quando o componente `HelloWorld` está inicializado na app. Veja:

```html
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
import  categories  from '@/services/categories';
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  mounted () {
    categories.getAll().then( result => {
      console.log(result);
    })
  }
};
</script>
```

Perceba que chamamos o método "getAll" diretamente do service. O que vem depois já é novidade. Se você não reconhece o `.then`, ele está relacionado a Promises, um conceito do Javascript. É preciso saber que qualquer chamada do frontend ao backend é assíncrono, ou seja, algo como:

```js
const items =  categories.getAll();
console.log(items);
```

É algo totalmente errado no "mundo" javascript. Só podemos "ler" o resultado do acesso ao backend quando isso for possível (pode demorar alguns segundos), e esse "retorno" é feito através de Promises. Basicamente, o método `then` será executado somente quando o backend retornar, e o resultado deste retorno é armazando na variável result, que pode ser lida pelo comando console.log.

Agora vamos testar a aplicação. Inicie-a com o comando `npm run serve` e vá até o Navegador. Abra a aplicação e abre o Chrome Dev Tools através da tecla F12. O que você verá é algo como:

<p align="center">
<img src="https://i.imgur.com/CtYXDgf.png">
</p>

Veja que o comando `console.log` exibiu o conteúdo da variável `result`, e que `result.data` contém o array de categorias que precisamos.

Até o momento já aprendemos a acessar o servidor e obter dados! Agora vamos aprender a exibí-los de forma coerente na aplicação.

# Comentários

O curso ainda está no começo, mas você pode dizer aí em baixo o que gostaria de ver nele! 

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