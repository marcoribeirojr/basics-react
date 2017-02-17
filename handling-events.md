## Manipulação de Eventos

Manipulação de eventos com React é parecido com a manipulação de eventos do DOM. A diferença é que ao invés da chamada do evento ser feita por uma função (`onclick="changeData()"`) é feita por uma string escrita em camel case (`onclick={changeData}`).

Ps.: A chamada de `preventDefault()` deve ser explícita no construtor do Component para evitar problemas.

### Uso
```
const React= require('react')
const ReactDOM=  require('react-dom')

class Button extends React.Component{
   constructor(props) {
    super(props);
    this.state = {isToggleOn: true};

    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState(prevState => ({
      isToggleOn: !prevState.isToggleOn
    }));
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        {this.state.isToggleOn ? 'ON' : 'OFF'}
      </button>
    );
  }
}

ReactDOM.render(
    <Button />,
    document.getElementById('root')
)
```

Note que a questão com o preventDefault() é resolvida no método construtor com `this.handleClick = this.handleClick.bind(this);` fazendo o `this` trabalhar com o callback.
