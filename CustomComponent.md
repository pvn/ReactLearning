### So lets create a component for the list item and also one for our input area

We'll add a new folder named *components* which will have our custom component source code.

Lets create two new files, one for **Product Entry (ProductInput.js)** 

and second for to show the **Product Lists (ProductLists.js)**


#### ProductInput.js

``````javascript
import React from 'react';

const ProductInput = props => {
    return (
        <View>
            <TextInput placeholder="Enter Product Name" style={styles.input}
                onChangeText={productInputHandler} value={productName}
            />
            <Button title="ADD" onPress={addProductHandler} />
        </View>
    )
}
``````

> But note that, 
> we're using a couple of components from React Native, we are using the **view** component, **text input** component, 
the **button component** and the **stylesheet component** to set up stylesheet object

``````javascript
import React from 'react';
import {View, Button, TextInput, StyleSheet} from 'react-native' //imported all the react-native basic stuffs
const ProductInput = props => {
    return (
        <View>
            <TextInput placeholder="Enter Product Name" style={styles.input}
                onChangeText={productInputHandler} value={productName}
            />
            <Button title="ADD" onPress={addProductHandler} />
        </View>
    )
}
``````

> But now, when we tap the button, that we add this, not having the **[state](https://github.com/pvn/ReactLearning/blob/master/State-Event.md)**
> So, whenever button is tapped, it should do something in app.js.

##### So lets bind [useState](https://reactjs.org/docs/hooks-state.html) to textfield input on **onChangeText** and import [useState](https://reactjs.org/docs/hooks-state.html).

``````javascript
//import useState
import React, { useState } from 'react';

//state management logic here with get and set entered product name 
//which we get from useState which we initialized with an empty string
const [productName, setProductName] = useState('')

//so this function which we connect to onChangeText and now with that, fetching the user input
const productInputHandler = (enteredText) => {
    setProductName(enteredText)
}
``````

#### Version(1):

``````javascript
import React, { useState } from 'react';
import {View, Button, TextInput, StyleSheet} from 'react-native'

const ProductInput = props => {

    //state management logic here with get and set entered product name which we get from useState which we initialized
    const [productName, setProductName] = useState('')

    //so this function which we connect to onChangeText and now with that, fetching the user input
    const productInputHandler = (enteredText) => {
        setProductName(enteredText)
      }

    return (
        <View>
            <TextInput placeholder="Enter Product Name" style={styles.input}
                onChangeText={productInputHandler} value={productName}
            />
            <Button title="ADD" onPress={addProductHandler} />
        </View>
    )
}
``````

#### Styling:
We are giving the styles for text field, or we can add the style for any component. 

So lets add styles here with **StyleSheet.create**, pass an object to that **StyleSheet.create** method

``````css
const styles = StyleSheet.create({

    input: {
        borderBottomColor: 'black',
        borderBottomWidth: 0.2,
        borderWidth:1,
        padding:10
      }
})
``````
