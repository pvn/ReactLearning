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

#### ProductInput.js (revised):

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

> To find out when a button is pressed in this component and in React, we do that by passing the function which the child component should execute eventually as a [**prop**](https://reactjs.org/docs/components-and-props.html) to the child component.

So here, we could add onAddProduct, that name is totally up to us.
``````javascript
<ProductInput onAddProduct/>
``````

> But This alone won't do anything but onAddProduct will now be received as a prop inside of product input and
it will point at a function, which means we can execute it as a function there.

``````javascript
<ProductInput onAddProduct={addProductHandler}/>
``````

Still we'd have an issue because in *addProductHandler*, because in **App.js** productName and that previously was managed in here but isn't anymore, because we moved to ProductInput.js

So now, In **App.js** *addProductHandler* should actually receive an argument which would be product title or whatever we want

And In ProductInput.js Button's onPress method, simply point at *prop.onAddProduct*

**ProductInput.js**
``````javascript
<Button title="ADD" onPress={props.onAddProduct.bind(this, productName)} />
``````

**App.js**
``````javascript
/*
const addProductHandler = () => {
    setProducts(products => [...products, { id: Math.random().toString(), value: productName }])
}
*/

// addProductHandler should actually receive an argument
const addProductHandler = productTitle => {
    setProducts(products => [...products, { id: Math.random().toString(), value: productTitle }])
}

``````


### Final Source Code:

#### ProductInput.js

``````javascript
import React, { useState } from 'react';
import {View, Button, TextInput, StyleSheet} from 'react-native'

const ProductInput = props => {

    //state management logic here with get and set entered product name which we get from useState which we initialized
    const [productName, setProductName] = useState('');

    //so this function which we connect to onChangeText and now with that, fetching the user input
    const productInputHandler = enteredText => {
        setProductName(enteredText)
    };
    return (
        <View>
            <TextInput 
                placeholder="Enter Product Name" 
                style={styles.input}
                onChangeText={productInputHandler} 
                value={productName}
            />
            <Button title="ADD" onPress={props.onAddProduct.bind(this, productName)} />
        </View>
    );
}

``````

#### App.js. (After replacing basic component with our custom component which can be easily integrate)

``````javascript
import ProductLists from './components/ProductLists';
import ProductInput from './components/ProductInput';

export default function App() {

  const [products, setProducts] = useState([])

  const addProductHandler = productTitle => {
    setProducts(products => [...products, { id: Math.random().toString(), value: productTitle }])
  }

  return (
    <View style={{ padding: 100 }}>
      
      // Custom component to get the input from user
      <ProductInput onAddProduct={addProductHandler}/>
      
      <FlatList
        keyExtractor={(item, index) => item.id}
        data={products}
        renderItem={itemData => (
          
          // Custom component to list out the product items
          <ProductLists title={itemData.item.value} />
      )}
      />
    </View>
  );
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
