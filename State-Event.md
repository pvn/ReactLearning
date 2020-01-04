### State and Events:
We will use the  [useState](https://reactjs.org/docs/hooks-state.html) hook for that which we import from React, not from ReactNative but from React. 
We will create two constant here **productText** and **setProductText** with the help of [useState](https://reactjs.org/docs/hooks-state.html)
``````javascript
const App: () => ReactNode = () => {

/*default we have initial state by passing empty string to useState 
	as user has not entered anything*/
const [productText, setProductText] = useState('')

  return (
	<View style={{padding: 100}}>

);
};
``````
Now we can bind this [useState](https://reactjs.org/docs/hooks-state.html) to textfield input, i.e. when user types a character, we will update the [useState](https://reactjs.org/docs/hooks-state.html) and we will save the entered product in the state. we can then access through getProduct. we will pass the getProduct value to back into the textfield input.

> That's this two way binding, it's so called **controlled component** which you also know from React

###### So lets bind [useState](https://reactjs.org/docs/hooks-state.html) to textfield input on **onChangeText**
``````javascript
const App: () => ReactNode = () => {

/*default we have initial state by passing empty string to useState 
	as user has not entered anything*/
const [productText, setProductText] = useState('')

return (
<View style={{padding: 100}}>
	<View>
		// onChangeText is a 'props' for TextInput
		<TextInput placeholder="Enter Product" style={styles.input} 
						onChangeText={productInputHandler} 
						value={getProductText}/>
 	</View>
	</View>
	);
};
``````

> onChangeText is a '**props**' for TextInput which takes a function '**productInputHandler**' that will execute on every change text by user to enter the product.

``````javascript
const App: () => ReactNode = () => {

/*default we have initial state by passing empty string to useState 
	as user has not entered anything*/
const [productText, setProductText] = useState('')

function productInputHandler(enteredText) {
	setProductText(enteredText)
}

 return (
<View style={{padding: 100}}>
	<View>
		// onChangeText is a 'props' for TextInput
		<TextInput placeholder="Enter Product" style={styles.input} 
						onChangeText={productInputHandler} 
						value={getProductText}/>
 	</View>
	</View>
	);
};
``````
> //NOTE: do not add the parenthesis to productInputHandler because we do not want to run this function execute immediately until user type any thing to it

We can write the function as constant and then we can use that constant anywhere 

    ~~function productInputHandler(enteredText) { setProductText(enteredText) }~~
	
	//can be written as constant
    const productInputHandler = (enteredText) => { 
		setProductText(enteredText) 
	}

**Summarize: **
> **onChangeText**={productinputhandler} **//on key stroke text**
**value**={getProductText} **// key stroke value setting back to textfield**

##### Similar to textinput, lets try with button and add the products to list by clicking on Add button

``````javascript
const App: () => ReactNode = () => {

/*default we have initial state by passing empty string to useState 
	as user has not entered anything*/
const [productText, setProductText] = useState('')
// to useState hook we are passing empty lists
const [products, setProducts] = useState([])

const addProductHandler = () => { 
	/* we are storing the product with some random key, 
	this would be useful while accessing the product using key*/
	setProducts[...products, {key: Math.random().toString(), value: products}]
}

 return (
<View style={{padding: 100}}>
	<View>
		// onChangeText is a 'props' for TextInput
		<TextInput placeholder="Enter Product" style={styles.input} 
						onChangeText={productInputHandler} 
						value={getProductText}/>
		<Button title="Add Product" onPress={addProductHandler}/>
 	</View>
	</View>
	);
};
``````


*Output*

> **[FlatList](https://facebook.github.io/react-native/docs/flatlist) component** has two parameters
*data* and *renderItem*

``````javascript
<FlatList 
      keyExtractor={(item, index) => item.id}
      data={courseGoals} 
      renderItem={itemData => (
        <View style={styles.listItem}>
          <Text>{itemData.item.value}</Text>
        </View> )}
/>
``````
