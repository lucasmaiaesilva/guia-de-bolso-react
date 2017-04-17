## Props

`Props` é o nome dado a propriedade (característica), de um componente, que, em geral, é usado para diferir itens entre um componente e outro contanto que **não seja necessário que o componente seja re-renderizado caso esses dados mudem na aplicação**.

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

Como pode ver na classe Mensagem, a propriedade name é 'pendurada' no objeto props e é acessada pela palavra chave `this` que é uma referência ao próprio objeto.

### Exceções de Props HTML

Pelo fato de existirem algumas palavras reservadas no Javascript, alguns props devem ser alterados quando passados, vejamos quais são:

#### class

A `class` dentro de um atributo HTML não pode ser usada dentro de um componente **JSX**, isso porque como já mencionado, o mesmo possui uma palavra reservada de **mesmo nome**, então substituímos por `className`.

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

#### for

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

Esse método existe para tratarmos props *default* de nosso componente, ou seja, quando não declaramos nenhuma propriedade no momento da chamada do código.

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

**Obs:** Ao passar algum outro tipo de dado em Javascript via props que não seja string, deve se fazê-lo colocando os dados entre chaves. Ex:


{% raw %}
```js
<Component number={2} checked={false} obj={ { a: 1, b:3 } }/>
```
{% endraw %}

### Proptype

Existe uma feature do React que nos permite de certo modo 'mascarar' os dados nele contidos a fim de dar uma maior segurança as propriedades passadas entre os Componentes.

```js
import React from 'react'
import PropTypes from 'prop-types'
// é necessária a instalação da lib prop-types

const MostrarDados = ({ nome, idade }) => (
  <div className='dados'>
    <p>Olá meu nome é {nome} e tenho {idade} anos.</p>
  </div>
)

MostrarDados.propTypes = {
  nome: PropTypes.string.isRequired,
  idade: PropTypes.number
}
```

Usando a propriedade `isRequired` ao final da configuração do Proptype, o componente entende que aquela propriedade é **obrigatória**, ou seja, se ela não for passada ao componente, o mesmo não irá se renderizar e vai mostrar uma mensagem de erro.

Vejamos alguns tipos de `propTypes` mais utilizados.

```js
MeuComponente.propTypes = {
  optionalArray: PropTypes.array,
  optionalBool: PropTypes.bool,
  optionalFunc: PropTypes.func,
  optionalNumber: PropTypes.number,
  optionalObject: PropTypes.object,
  optionalString: PropTypes.string,

  // Um elemento react
  optionalElement: PropTypes.element,

  // Declarando um objeto e setando tipos de proptypes
  // dentro do próprio objeto
  optionalObjectWithShape: PropTypes.shape({
    color: PropTypes.string,
    fontSize: PropTypes.number
  })
}
```
Fazendo dessa forma todos os dados passados  para o componente via props serão validados e uma mensagem de erro é mostrada caso as regras estabelecidas não sejam cumpridas. Essa é a função do `propTypes`.
