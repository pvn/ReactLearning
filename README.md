# React Native
   A React Native app is all about using **components** and then adding the **right layout**, the **right structure**


### Required tools
    Node
    Watchman
    React Native CLI
    XCode, Android Studio
    Yarn package manager


### For Development OS: **macOS**     Target OS: **iOS**

#### Installation of required tools one by one
1 - Node installation
        **brew install node**
    
2 - Watchman installation
        **brew install watchman**

3 - React Native CLI
        **npm install -g react-native-cli**

4 - Install XCode or Android Studio
        **Install XCode or Android Studio from the official website.**

5 - Install yarn package manager  (optional)
        **brew install yarn (https://yarnpkg.com/lang/en/docs/install/#mac-stable**
        
### Basic understanding of yarn and npm

   **npm** default package manager for Node.js
   
   **yarn** default package manager release by Facebook

    npm : Every npm install automatically add installed modules to both package.json and package-lock.json. This file is meant to be committed into the version control you are using.

    yarn: Yarn introduced workspaces. In combination with Lerna, it gives package authors a powerful toolset to manage the dependencies and of projects and also enables publishing to be a lot easier.



### [Styling:](https://github.com/pvn/ReactLearning/blob/master/Styling.md)

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
