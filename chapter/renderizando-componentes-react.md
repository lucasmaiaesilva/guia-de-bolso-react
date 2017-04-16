## Renderizando componentes

Basicamente existem 3 formas de se renderizar os Componentes React são elas:

* React.createClass()
* Funções puras
* Classes (ES2015)

### React.createClass()

A função `createClass` aceita um objeto por parâmetro e as `features` do React são escritas como **propriedades** desse objeto. Vejamos um exemplo:

```js
var Title = React.createClass({
  defaultProps: {
    valorInicial: ''
  },
  render: function () {
    return (
      <h1>Olá mundo</h1>
    )
  }
})
```

No momento de escrita desse guia, essa maneira de se escrever React não é a mais recomendada, uma vez que com o surgimento do ES6 vieram novas formas menos *verbosas* de se escrever componentes.

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

Podemos ainda remover a palavra chave return, juntamente com os parênteses que também obteremos o mesmo resultado, graças as Arrow Functions do ES2015.

```js
const Title = () => <h1>Olá meu povo!</h1>
```

#### Passando props as funções puras

Como não estamos utilizando classes, obviamente não utilizaremos a palavra reservada `this`, pois não estamos mais referenciando um objeto. Nesse caso então basta colocar o objeto props dentro do parâmetro da arrow function, veja como ficaria:

```js
const Title = (props) => (
  <h1>Olá {props.name}</h1>
)

const App = () => <div> <Title name='Lucas' /> </div>
```

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

### Classes (ES2015)

Para renderizar um componente usando classes, basta criar uma classe e extendê-la a partir de um React Component, isso faz parte de um conceito que surgiu com a POO (Programação Orientada a Objetos), chamado de *herança*.

Vejamos como renderizar um componente a partir de uma classe:

```js
import React, {Component} from 'react'

class App extends Component {
  render () {
    return (
      <h1>Alô {this.props.mensagem}!</h1>
    )
  }
}

App.defaultProps = {
  mensagem: 'criançada'
}
```

Como pode perceber, neste tipo de renderização voltamos a utilizar a palavra chave `this`, pois estamos falando de renderização de componente via `instanciação de objetos`.

### Prop Key

A Propridade Key é usada quando replicamos um mesmo componente *mais de uma vez*, geralmente por iteração de arrays. O React precisa dessa propriedade para renderizar e entender que cada chave que ele tiver possui uma característica *única*, portanto *não* podemos utilizar valores repetidos dentro da prop `key`.

```js
let arr = ['pedro', 'carlos', 'joão']

return (
  <div>
    { arr.map( (item, index) => (
      <Mensagem nome={item} key={index} />
    ) ) }
  </div>
)
```

A propriedade `key`, não deve ser trabalhada na aplicação, portanto ela deve servir somente como um parâmetro para o React, para que ele possa se "orientar" na hora de renderizar os componentes.

> Obs: A propriedade Key não deve jamais, ser duplicada.
