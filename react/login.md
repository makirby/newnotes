#Login View

- create login.js file
- enable strict mode `'use strict'`

##Creating the component

To bring in react use `var React = require('react-native')`
This will bring in the code for react.

Every component in react needs to have a render function. Example below:

`
var {
    AppRegistry,
    StyleSheet,
    Text,
    View,
} = React;

var Login = React.createClass({ 
    render: function(){
        return(
            <View style={styles.container}
                <Image style='{styles.logo}'
                source={require('image!Octocat')} />
                <Text style={styles.heading}>
                    App Heading
                </Text>
                <TextInput style={styles.input} 
                    placeholder = "username"/>
                <TextInput style={styles.input}
                    placeholder = "password"
                    secureTextEntry="true" />
           </View>
        );
    } 
});

var styles = StyleSheet.create({
    container: {
        backgroundColor : 'color',
        flex: 1,
        paddingTop: 40
    },
    logo: {
        width: 66,
        height: 55
    }
})

module.exports = Login; //this exports the login module (duh)

`
###To Note
- images have to be added through xcode
- The react module must be exported through `module.exports`
- Can use the secureTextEntry field to hide password

