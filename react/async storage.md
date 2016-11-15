#Using the Async storage component

This component can be used to store user credentials and other small bits of information about the user

##Using AsyncStorage to store!
We can bring it into our application using `var AsyncStorage = require('react-native').AsyncStorage`
Once this is done there are a couple of methods that can be used to save the data i.e to store credentials we could do:

`
.then((results) => {
    AsyncStorage.multiSet([
        ['auth', encodedAuth],
        ['user', JSON.stringify(results)]
        ], (err) => {
            id(err){
                throw err;
            }

            return cllbk({success: true});
        })
})
`

This example is ripped from the tutorial as a part of the auth.js file.
The multiSet method can be used to set a key value pair array that will maintain the values on the next use.

##Retrieving the data from async store

Pretty simple, just like Async.multiSet we can use something called Async.multiGet!

`
   getAuthInfo(cb){
       AsyncStorage.multiGet([authkey, userKey], (err, val) => {
           if(err){
               return cb(err);
           }

           if(!val){
               return cb();
           }

           var zippedObj = _.zipObject(val); //lodash function

           if(!zippedObj[authKey]){
               return cb();
           }

           var authInfo = {
               header: {
                   Authorzation: 'Basic ' + zippedObj[authKey] 
               },
               user: JSON.parse(zippedObj[userKey])
           }

           return cb(null, authInfo);
       });
   }   
`

Above is an example of a authorisation store using the AsyncStorage component.
The user authorisation keys and values are pulled from the asyncstore. 
This can be reused throughout an application.