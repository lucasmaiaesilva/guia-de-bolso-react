## Children

A propriedade Children existe para quando precisamos passar informações de um Componente ao outro como conteúdo do HTML, é um pouco diferente da abordagem convencional do React, porém é extremamente útil, definitivamente criamos uma TAG quando usamos essa abordagem.

```js
class App extends Component {
  render () {
    return (
      <div>
        <Card>
          <h2>Titulo do Card</h2>
          <p>Descrição do Card</p>
        </Card>
      </div>
    )
  }
}

const Card = ( {children} ) => (
  <div className='card'>
    {children}
  </div>
)

```
