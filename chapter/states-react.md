## States

A diferença básica entre um estado (state) de aplicação e uma propriedade daquela aplicação é relacionado a mudança. Uma propriedade é uma coisa que não muda com frequência, já o estado sim. Basta fazermos uma analogia ao nosso mundo real. Por exemplo uma propriedade do Lucas é que ele tem 1.8, porém seu estado atual é de tristeza, viram?

No React, toda vez que um estado é alterado o componente é renderizado novamente. Já em props isso não acontece.

```js
class App extends Component {
  constructor () {

    // função que puxa as configurações da classe Component
    super()

    // setando um estado inicial para as propriedades
    this.state = {
      text: 'texto original'
    }
  }

  render () {
    <div onClick={() => (this.setState({
      text: 'texto modificado'
    }))}>
      {this.state.text}
    </div>
  }
}
```

Como dito quando alterado o estado, o componente automaticamente irá **re-renderizar**, ou seja, será renderizado novamente, aplicando as mudanças necessárias requeridas pelo método `setState`.

### Fluxo de Dados unidirecional

O React sempre renderiza informação vinda de pai pra filho no formato de `props`, porém no componente pai onde se é requerido um certo dinamismo na aplicação, esses dados muito provavelmente em formato de `states`. 