#Login module is pretty dumb

##Convert login to ES6

Change the class from React.createClass
`
 class Login extends Component {
    constructor(props){
        super(props);
    }
}
`
##Adding functionality to textboxes
We can add functionality to the textbox components using very similar syntax to browser based apps
i.e to assign the value of the input to the 'state' we can use the arrow function inline

`
<TextInput
    onChangeText={(text) => this.setState({username : text})}>
</TextInput>
`

##Adding functionality to a button (TouchableHighlight)

`
<TouchableHighlight 
    onPress={this.onLoginPressed.bind(this)}>
    <Text style={styles.buttonText}>Log In</Text>
</TouchableHighlight>

onLoginPressed(){

}

`
To note:
- we can call the function onLoginPressed using the onPress attribute
- the function must be bound to 'this'

##ActivityLoader components

Can use this component to show that async activity is occuring, especially useful when sending 
http requests

`


constructor(props){
    super(props);

    this.state = {
        showProgress: false
    }
}

<ActivityIndicatorIOS 
    animating={this.state.showProgress}
    size="large"
/>

onLoginPressed(){
    console.log('Attempting to log in with username ' + this.state.username)
    this.setState({ showProgress : true});
}

`
In this example its important to note that 
- the state is set by the js function that is called when the button is pressed.
- ActivityIndicatorIOS can be used just like any other component inc styling etc
- it must be declared like other components
- the animating property is a boolean
