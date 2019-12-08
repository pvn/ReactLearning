### Styling:

it's important to understand that React Native doesn't use web technologies, it doesn't use HTML, it uses Javascript arguably but doesn't use HTML and it also doesn't use CSS, so CSS which you use for styling in the web is not supported in React.

Native but it gives you styling commands, styling configuration you can add to your components, so to these components that are built into React Native either with the help of **inline styles** or with so-called **stylesheet objects** and there, 

We can write these style instructions in Javascript but use a syntax which is based on CSS. 
So it's not directly related to CSS but of course it's influenced by CSS, many of the instructions you use here are inspired by CSS and many of the rules or of the properties.

*Most components in React Native support the **style** property*

the keys are for style property names and the values are the values for these style properties, and these style property names are influenced by CSS.

Ex:
 ```css
<View styles={{ padding: 10 }}
const styles = StyleSheet.create({
	scrollView: {
		backgroundColor: Colors.lighter,
	},
	body: {
		backgroundColor: Colors.yellow,
	}
});
```
