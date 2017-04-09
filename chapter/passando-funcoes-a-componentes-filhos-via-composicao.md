## Passando Funções a componentes filhos via composição

Suponhamos que tenhamos diferentes tipos de formulário em uma aplicação e cada um deles tenha que ser feito um submit de maneira específica. Como fazer pra manter um padrão de componente porém com uma função específica em cada um.

Vejamos um exemplo prático de como utilizar.

```js
const Formulario = ({ children, submitFormulario }) => (
  <form>
    <FormContent onClick={ submitFormulario }>
      {children}
    </FormContent>
  </form>
)

const FormLogin = () => (
  <Formulario handleClick={ () => alert('formulário inativo no momento') }>
    <input type='text' name='usuario' />
  </Formulario>
)
```

Dessa forma podemos usar o Componente 'Formulário' várias vezes e reaproveitando os elementos especificando atributos e métodos diferentes a cada nova chamada de componente.