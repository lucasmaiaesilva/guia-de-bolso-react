# Guia prático sobre ReactJS

Este guia tem como objetivo principal armazenar informações úteis e práticas sobre a biblioteca ReactJS.

Algumas features usadas juntamente com o React.

* ES6
* Testes
* Flux
* Redux

## Sobre o React

## Props

Props é o nome dado a propriedade (característica), de um componente, em geral é usado para diferir itens entre um componente e outro, contanto que eles **não seja necessário que o componente seja re-renderizado caso esses dados mudem na aplicação**.

### Usando Props em componentes React

```js

'use strict'

import React from 'react'

class Mensagem extends React.Component {
  render () {
    return (
      <h1>Olá {this.props.name}! </h1>
    )
  }
}

class App extends React.Component {
  render () {
    return (
      <div>
        <Mensagem name='Lucas Maia' />
      </div>
    )
  }
}

```

Como pode ver na classe Mensagem, a propriedade name é 'pendurada' no objeto props e acessada pela palavra chave `this` que é uma referência ao próprio objeto.

### Exceções de Props HTML
Pelo fato de existirem algumas palavras reservadas no Javascript, alguns props devem ser alterados quando passados, vejamos quais são:

#### Class

A `class` dentro de um atributo HTML não pode ser usada dentro de um componente JSX, isso porque como já mencionado, o mesmo possui uma palavra reservada de **mesmo nome**, então substituímos para `className`.

```js
class App extends React.Component {
  render () {
    return (
      <div className='container'>
        <h1>Olá mundo!</h1>
      </div>
    )
  }
}
```

Nesse exemplo fica nítido que a palavra `class` está sendo usada no início para definir que estamos criando uma classe em Javascript, portanto não podemos usar esse mesmo nome como atributo HTML da div.

#### For

É comum quando utilizamos uma label em um formulário, utilizarmos a palavra `for`, para caracterizar que aquele elemento pertence aquela determinada label.

Ex: `<label for='email'>`.

Nesse caso então substituímos o `for` por `htmlFor`.

```js
// código dentro de um componente JSX

<div className='form'>
  <label htmlFor='nome'> Digite seu nome: </label>
  <input type='text' id='nome' />
</div>
```

### getDefaultProps

Esse método existe para tratarmos Props *default* de nosso componente, ou seja, quando não declaramos nenhuma propriedade no momento da chamada do código.

Veja o exemplo no código:

```js

'use strict'

import React from 'react'

class Mensagem extends React.Component {

  getDefaultProps () {
    return (
      name: 'mundo'
    )
  },

  render () {
    return (
      <h1>Olá {this.props.name}! </h1>
    )
  }
}

class App extends React.Component {
  render () {
    return (
      <div>
        <Mensagem />
        <Mensagem name='Lucas Maia' />  
      </div>
    )
  }
}

```

Dentro da classe App, podemos ver 2 chamadas do Component 'Mensagem', a primeira delas retornará a Mensagem 'Olá mundo', porque não especificamos nenhuma `prop` name então o método `getDefaultProps` nos fornece um name padrão e a segunda retornará a mensagem 'Olá Lucas Maia'.

> Obs: Ao passar algum outro tipo de dado em Javascript via Props que não seja string, deve se fazê-lo colocando os dados entre chaves. Ex: <Component number={2} checked={false} obj={{a: 1, b:3}}/>

## Renderizando componentes

Basicamente existem 3 formas de se renderizar os Componentes React são elas:

* React.createClass()
* Funções puras
* Classes (ES2015)

### React.createClass()

Usada nos exemplos anteriores, uma maneira de se criar componentes usando ES5.

### Funções puras

Podemos usar as funções puras para criar os componentes, de maneira simples apenas as declarando.

```js
const Title = function () {
  return (
    <h1>Olá meu povo!</h1>
  )
}
```

Como são funções podemos também usar as arrow functions do ES2015

```js
const Title = () => {
  return (
    <h1>Olá meu povo!</h1>
  )
}
```

Podemos ainda remover a palavra chave return, juntamente com os parênteses que também obteremos o mesmo resultado.

```js
const Title = () => <h1>Olá meu povo!</h1>
```

Lindo né?

#### Passando props as funções puras

Como não estamos utilizando classes, obviamente não utilizaremos a palavra reservada `this`, pois não estamos mais referenciando um objeto. Nesse caso então basta colocar o objeto props dentro do parâmetro da arrow function, veja como ficaria:

```js
const Title = (props) => (
  <h1>Olá {props.name}</h1>
)

const App = () => <div> <Title name='Lucas' /> </div>
```

Fala sério, agora ficou bem mais simples de entender né não?

#### Utilizando defaultProps em funções puras

Para utilizarmos métodos que antes pertenciam as classes em funções puras basta criá-los como se fossem funções estáticas do Title.

```js
const Title = (props) => (
  <h1>Olá {props.name}</h1>
)

Title.defaultProps = {
  name: 'Desconhecido'
}
```
