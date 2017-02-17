
## Renderização condicional

A renderização condicional diz respeito a usar condicionais do Javascript para renderizar ou não componentes React e/ou selecionar o tipo de componente que será renderizado.

### Uso

```  
const React= require('react')
const ReactDOM=  require('react-dom')

const LoginButton = props => {
    return (
        <button onClick={props.onClick}>
            Login
        </button>
    )
}

const LogoutButton = props => {
    return (
        <button onClick={props.onClick}>
            Logout
        </button>
    )
}

const UserGreeting = props => {
    return (
        <h1>Seja bem-vindo!</h1>
    )
}

const GuestGreeting = props => {
    return (
        <h1>Faça seu login.</h1>
    )
}

const Greeting = props => {
    const isLoggedIn = props.isLoggedIn
    if(isLoggedIn){
        return(
            <UserGreeting />
        )
    }
    return(
        <GuestGreeting />    
    )
}

class LoginControl extends React.Component{
   constructor(props){
       super(props)
       this.state = {isLoggedIn : false}

       this.handleLoginClick = this.handleLoginClick.bind(this)
       this.handleLogoutClick = this.handleLogoutClick.bind(this)
   }

   handleLoginClick(){
       this.setState(prevState => ({
           isLoggedIn : !prevState.isLoggedIn
       }))
   }

   handleLogoutClick(){
       this.setState(prevState => ({
           isLoggedIn : !prevState.isLoggedIn
       }))
   }

   render(){
       const isLoggedIn = this.state.isLoggedIn
       let button = false

       if(isLoggedIn){
           button = <LogoutButton onClick={this.handleLoginClick} />
       }
       else{
           button = <LoginButton onClick={this.handleLogoutClick} />
       }
       return(
            <div>
                <Greeting isLoggedIn={isLoggedIn} />
                {button}
            </div>
        )
   }

}

ReactDOM.render(
    <LoginControl />,
    document.getElementById('root')
)
```  
