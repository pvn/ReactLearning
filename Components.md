#### Custom Component:

We will learn, how to create our own custom components which can be used multiple places whereever is required.
So lets add a new folder called 'component' inside a project which will have our own custom components.

Before learning the custom component, lets first understand about the most used component in ReactNative called [FlatList](https://facebook.github.io/react-native/docs/flatlist).

#### [FlatList](https://facebook.github.io/react-native/docs/flatlist) has two important properties

    first property is the *data* property where you point at your input data 
    and this should point at an array
    
    second property is *renderItem*, that takes a function which is called for every item

For e.g.

```javascript
<Flatlist data={products}
renderItem = {product => (
....  // renderItem has to return a component so here we will return a View component for example.
....
)}
/>
```
See the following code where renderItem return a View component.
```javascript
<Flatlist data={products}
renderItem = {product => (
<View style={styles.listItem}>
    <Text>{product.item.value}</Text>
</View>
keyExtractor={product => product.id}
)}
/>
```
