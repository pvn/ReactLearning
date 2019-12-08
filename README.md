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



### Styling:

it's important to understand that React Native doesn't use web technologies, it doesn't use HTML, it uses Javascript arguably but doesn't use HTML and it also doesn't use CSS, so CSS which you use for styling in the web is not supported in React.

Native but it gives you styling commands, styling configuration you can add to your components, so to these components that are built into React Native either with the help of **inline styles** or with so-called **stylesheet objects** and there, 

We can write these style instructions in Javascript but use a syntax which is based on CSS. 
So it's not directly related to CSS but of course it's influenced by CSS, many of the instructions you use here are inspired by CSS and many of the rules or of the properties.

*Most components in React Native support the **style** property*

the keys are for style property names and the values are the values for these style properties, and these style property names are influenced by CSS.

Ex:

`<View styles={{**padding: 10**}}`
