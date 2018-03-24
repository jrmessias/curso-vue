
<img src="logo.png" style="float:right">

# Sumário

<!-- TOC -->

- [Sumário](#sumário)
- [Sobre este curso](#sobre-este-curso)
    - [Porque existe a separação entre frontend e backend?](#porque-existe-a-separação-entre-frontend-e-backend)
- [O que é Vue?](#o-que-é-vue)
- [Preparando o ambiente](#preparando-o-ambiente)

<!-- /TOC -->

# Sobre este curso

Este mini curso tem como objetivo introduzir o Framework Javascript Vue.js para o desenvolvimento de aplicações que chamamos de SPA - *Single Page Applications*, isto é, aplicações de página única. Este conceito é o inverso dos sistemas Web mais comuns onde cada funcionalidade é uma página ou uma requisição que contém uma página completa. No desenvolvimento atual, existe uma separação muito clara entre frontend e backend, e o Vue.js entra no papel de framework frontend.

## Porque existe a separação entre frontend e backend?

O desenvolvimento de sistemas vem passando ao longo dos últimos anos uma mudança significativa, motivada principalmente pela entrada dos dispositivos mobile como principal meio de uso e acesso aos sistemas. Antigamente, um sistema poderia ser 100% web e estaria atendendo aos requisitos básicos do cliente, mas hoje em dia o sistema deve ser capaz de ser web e mobile, independente do tipo de dispositivo mobile. 

A comunicação entre *frontend* e *backend* é realizada através de [RESTfull](https://pt.wikipedia.org/wiki/REST). Basicamente, o *frontend* acessa o *backend* via ajax, e o *backend* responde com algum dado no formato Json.


# O que é Vue.js?

O Vue (a mesma pronúncia de *view* no inglês, isto é, *víu*) é um framework javascript que "cuida" de toda a parte do desenvolvimento *frontend*. Através dele será possível criar todas as telas de um sistema, contendo formulários, campos, tabelas, abas, etc. Além disso, existem diversas bibliotecas para o Vue que maximizam as suas funcionalidades. O Vue é um concorrente direto de outros dois frameworks, Angular e React. Estes 3 frameworks hoje em dia estão entre os prediletos para o desenvolvimento *frontend*.

O Vue exige um pouco de conhecimento em HTML, JavaScript e CSS, que são as três bases do desenvolvimento web, mas não é obrigatório que você seja um expert para poder continuar o curso. Será um "passeio no parque" se você já conhece bem Javascript e está familiarizado com ES2016. 

Se você começar a estudar o Vue pela documentação oficial (que aliás é ótima, e em português), verá coisas do tipo:

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

Nosso curso aborda o Vue de uma forma diferente da documentação oficial, de forma a prepará-lo para o "mundo real", usando o que há de melhor no framework. Isso significa que, quando começarmos a aprender Vue, estaremos usando um *template* pronto com vários arquivos prontos, tudo funcionando de forma sincronizada para que se possa obter o máximo de proveito do Vue. Para chegarmos nesse ponto, precisamos primeiro preparar o nosso ambiente de desenvolvimento.

# Preparando o ambiente


