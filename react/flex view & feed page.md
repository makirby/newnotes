#Flex view and how its used in the feed page

- Alot of the items can be reused from the appcontainer.js

`class Feed extends Component {}`

Exactly the same as used in any of the other components.

To instantiate the listview we use the component 'ListView', this component requires a datasource
which we have to set up in the constructor:

`var ds = new ListView.DataSource({rowHasChanged : (r1, r2) => r1 != r2})`

We also will add the information in the datasource to the application state e.g:

`this.state = {dataSource: ds.cloneWithRows(['A', 'B', 'C'])};`

The view for this page will again be contained in a flexbox, with it starting at the top and 
working down the page. This can be configured in the stylesheet like so:

`
feed :{
    flex: 1,
    justifyContent: 'flex-start'
}
`
To wire up the ListView we have to set the dataSource for the component & a function for the renderRow
property.

To set the datasource in this example:

`<ListView dataSource={this.state.dataSource}/>`

The renderRow function can take 3 parameters `renderRow(rowData, sectionID, rowID)` and can be attached to 
the ListView element in a very similar way to the other JS bindings:

`<ListView renderRow={this.renderRow.bind(this)}/>`

With the renderRow function containing data like so:

`
renderRow(rowData){
    return <Text>
        {rowData.item}
    </Text>
}
`

To populate the data in the ListView we can create a function to fetch the data from the service:

`
fetchFeed(){
    require('./AuthService').getAuthInfo((err, authInfo) => {
        var url = 'blah blah.com'
            + authInfo.user.login
            + 'events'

        fetch(url, {
            headers: authInfo.header
        })
        .then((response) => response.json())
        .then(responseData) => {
            var feedItems = responseData;

            this.setState({
                dataSource: this.state.dataSource.cloneWithRows(feedItems)
            });
        }}
    })
}
`
##Things to note here

- the fetchFeed can be enhanced to make use of the loading indicator the same 
way that we have for other pages through the use of a `state.showProgress` 
variable
- Fetch method is returning promises for the specified items, we can alter/check the data
in the responseData handling part of the code
- We set the state dataSource (which is what the ListView uses to populate the rows) in the
responseData handling promise.







