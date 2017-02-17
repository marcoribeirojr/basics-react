## Formulários

O React controla as informações dos campos de um formulário de forma um tanto diferente do que de costume. Eles chamam de _Controlled Components_ o método utilizado para modificar o comportamento padrão dos elementos e fazer seu controle através do próprio React.  

# Uso

```
const React= require('react')
const ReactDOM=  require('react-dom')

class Form extends React.Component{
    constructor(props){
        super(props)
        this.state = {value : ''}

        this.handleChange = this.handleChange.bind(this)
        this.handleSubmit = this.handleSubmit.bind(this)
    }

    handleChange(event){
        this.setState({value : event.target.value})    
    }

    handleSubmit(event){
       alert(this.state.value)
       event.preventDefault()
    }

    render(){
        return (
            <form onSubmit={this.handleSubmit}>
                <label>
                    Name:
                    <input type="text" value={this.state.value} onChange={this.handleChange} />
                </label>
                <input type="submit" value="Enviar" />
            </form>
        )
    }

}


ReactDOM.render(
    <Form />,
    document.getElementById('root')
)
```

Este é um exemplo de uso com um simples input text. Caso queira pode consultar a [documentação oficial](https://facebook.github.io/react/docs/forms.html) para saber como lidar com outros tipos de elementos. O uso é análago a este em sua maioria.
