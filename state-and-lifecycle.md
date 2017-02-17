## State e Lifecycle

### State
State se refere ao atual estado das informações dos Props.

### Lifecycle

Lifecycle re refere à atualização do State.

Deve-se apenas atualizar o estado dos Props (atualização das informações) através de um Lifecycle.

### Uso

```
const React= require('react')
const ReactDOM=  require('react-dom')

class Clock extends React.Component{
    constructor(props){
       super(props)
       this.state = {date: new Date()}
    }

    componentDidMount(){
        this.timerID = setInterval(
            () => this.tick(),
            1000
        )
    }

    componetDidUnmount(){
        clearInterval(this.timerID)
    }

    tick(){
       this.setState({
           date: new Date()
       })
    }
    render(){
        return(
            <div>
                <h2>São exatamente: {this.state.date.toLocaleTimeString()}.</h2>
            </div>
        )
    }
}

ReactDOM.render(
    <Clock />,
    document.getElementById('root')
)

```

Neste caso o State é definido no construtor e o LifeCycle (atualização do State) através do método `tick()`.
