#Creating the app container/tab view

- create a new file called AppContainer.js
- this example below contains all the components that are needed to create a tab view in React Native
`
var {
    Text,
    View,
    Component,
    StyleSheet,
    TabBarIOS
} = React;

class AppContainer extends component {
    constructor(props){
        super(props);

        this.state = {
            selectedTab: 'feed'
        }
    }

    render(){
        return(
            <TabBarIOS style={styles.container}>
                <TabBarIOS.Item
                title = "Feed"
                selected={this.state.selectedTab == 'feed'}
                icon={require('image!inbox')}
                onPress={() => this.setState({selectedTab: 'feed'})}
                />
                    <Text style={styles.welcome}> This is tab 1! </Text>
                </TabBarIOS.Item>
                <TabBarIOS.Item
                title = "Search"
                selected={this.state.selectedTab == 'search'}
                icon={require('image!search')}
                onPress={() => this.setState({selectedTab: 'search'})}
                />
                    <Text style={styles.welcome}> This is tab 2! </Text>
                </TabBarIOS.Item>
            </TabBarIOS>            
        );
    }
}

module.exports = AppContainer;
`
##To Note 

- the TabBarIOS component must contain all the TabBarIOS.Item elements within it