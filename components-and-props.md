## Components e Props

### Components

São componentes isolados que pode ser reaproveitados, funcionam de forma independente e são adicionados no DOM. Os components podem ser representados por Funções ou Classes.

### Props
São as informações que vão ser disponibilizados e/ou manipuladas nos components.

### Uso

```
const React = require('react')
const ReactDOM =  require('react-dom')

class Hello extends React.Component{
  render(){
    return(
      <h1>Olá, {this.props.name}!</h1>
    )
  }
}

const element = <Hello name="Fulano"/>

ReactDOM.render(
    element,
    document.getElementById('root')
)
```
