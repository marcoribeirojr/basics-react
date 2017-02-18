## Lifting State Up

Lifting state up é o compartilhamento do estado (valor) de um componente pai com seus componentes ancestrais. Diferente de outros frameworks que usam o _two way data binding_, o React compartilha de forma diferente o estado de seus componentes. O componente mais acima (pai) compartilha o estado que será comumente usado por seus ancestrais (filhos) e esse compartilhamento acontece no momento da renderização. Qualquer alteração no estado do componente pai é refletido nos filhos.

### Uso

```

const React= require('react')
const ReactDOM=  require('react-dom')

const BoilingVerdict = props => {
  if (props.celsius >= 100) {
    return <p>A água ferve.</p>
  }
  return <p>A água não ferve.</p>
}

const toCelsius = fahrenheit => {
  return (fahrenheit - 32) * 5 / 9
}

const toFahrenheit = celsius => {
  return (celsius * 9 / 5) + 32
}

const tryConvert = (value, convert) => {
    const input = parseFloat(value)
    if(Number.isNaN(input)){
        return ''
    }
    const output = convert(input)
    const rounded = Math.round(output * 1000) / 1000
    return rounded.toString()
}

const scaleNames = {
    c : 'Celsius',
    f : 'Fahrenheit'
}

class TemperatureInput extends React.Component {
  constructor(props) {
    super(props)
    this.handleChange = this.handleChange.bind(this)
  }

  handleChange(e) {
    this.props.onChange(e.target.value)
  }

  render() {
    const value = this.props.value
    const scale = this.props.scale
    return (
      <fieldset>
        <legend>Informe a temperatura em {scaleNames[scale]}:</legend>
        <input value={value} onChange={this.handleChange} />
      </fieldset>
    )
  }
}

class Calculator extends React.Component {
  constructor(props) {
    super(props)
    this.handleCelsiusChange = this.handleCelsiusChange.bind(this)
    this.handleFahrenheitChange = this.handleFahrenheitChange.bind(this)
    this.state = {value: '', scale: 'c'}
  }

  handleCelsiusChange(value) {
    this.setState({scale: 'c', value})
  }

  handleFahrenheitChange(value) {
    this.setState({scale: 'f', value})
  }

  render() {
    const scale = this.state.scale
    const value = this.state.value
    const celsius = scale === 'f' ? tryConvert(value, toCelsius) : value
    const fahrenheit = scale === 'c' ? tryConvert(value, toFahrenheit) : value

    return (
      <div>
        <TemperatureInput scale="c" value={celsius} onChange={this.handleCelsiusChange} />
        <TemperatureInput scale="f" value={fahrenheit} onChange={this.handleFahrenheitChange} />
        <BoilingVerdict celsius={parseFloat(celsius)} />
      </div>
    )
  }
}

ReactDOM.render(
    <Calculator />,
    document.getElementById('root')
)
```
Note que no trecho do código `const scale = this.state.scale` e `const value = this.state.value` é o momento em que o estado do componente `<Calculator />` é commpartilhado com seus ancestrais `<TemperatureInput />`.
