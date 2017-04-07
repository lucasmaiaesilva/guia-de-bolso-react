# Guia prático sobre ReactJS

Este guia tem como objetivo principal armazenar informações úteis e práticas sobre o Framework ReactJS.

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
