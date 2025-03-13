# React Native Assessment Challenge: Shopping Cart with Context API

### Task: Complete a shopping cart implementation using React Context API to manage global state.
### Requirements:
   1. Implement a CartContext that manages products in cart across multiple screens
   2. Create a cart provider that exposes methods to add, remove, and update cart items
   3. Build screens that consume the context (ProductList and Cart)
   4. Calculate cart totals (items count, subtotal)
   5. Implement persistence using AsyncStorage
   6. Add proper error handling and loading states

### Time limit: 60 minutes

```
// File structure:
// ├── contexts/
// │   └── CartContext.js (to be implemented)
// ├── screens/
// │   ├── ProductListScreen.js (partially implemented)
// │   └── CartScreen.js (to be implemented)
// ├── components/
// │   ├── ProductItem.js (implemented)
// │   └── CartItem.js (to be implemented)
// └── App.js (partially implemented)
```

Here's an example of context API usage:
```
import React, { useState, createContext, useContext } from "react"
import { createRoot } from "react-dom/client"

const languages = ["JavaScript", "Python"]
const LanguageContext = createContext({
    languages,
    language: languages[0],
    setLanguage: () => {},
})

const MainSection = () => {
    const { languages, language, setLanguage } = useContext(LanguageContext)
    const currentIndex = languages.indexOf(language)
    const toggleLanguage = () =>
        currentIndex === languages.length - 1
            ? setLanguage(languages[0])
            : setLanguage(languages[currentIndex + 1])

    return (
        <div>
            <p id="favoriteLanguage">{`Favorite programming language: ${language}`}</p>
            <button id="changeFavorite" onClick={toggleLanguage}>
                Toggle language
            </button>
        </div>
    )
}

const App = () => {
    const [language, setLanguage] = useState(languages[0])
    return (
        <LanguageContext.Provider value={{ languages, language, setLanguage }}>
            <MainSection />
        </LanguageContext.Provider>
    )
}

const root = createRoot(document.getElementById("root"))
root.render(<App />)
```



## This is an [Expo](https://expo.dev) project created with [`create-expo-app`](https://www.npmjs.com/package/create-expo-app).

## Get started

1. Install dependencies

   ```bash
   npm install
   ```

2. Start the app

   ```bash
    npx expo start
   ```

In the output, you'll find options to open the app in a

- [development build](https://docs.expo.dev/develop/development-builds/introduction/)
- [Android emulator](https://docs.expo.dev/workflow/android-studio-emulator/)
- [iOS simulator](https://docs.expo.dev/workflow/ios-simulator/)
- [Expo Go](https://expo.dev/go), a limited sandbox for trying out app development with Expo

You can start developing by editing the files inside the **app** directory. This project uses [file-based routing](https://docs.expo.dev/router/introduction).

## Get a fresh project

When you're ready, run:

```bash
npm run reset-project
```

This command will move the starter code to the **app-example** directory and create a blank **app** directory where you can start developing.

## Learn more

To learn more about developing your project with Expo, look at the following resources:

- [Expo documentation](https://docs.expo.dev/): Learn fundamentals, or go into advanced topics with our [guides](https://docs.expo.dev/guides).
- [Learn Expo tutorial](https://docs.expo.dev/tutorial/introduction/): Follow a step-by-step tutorial where you'll create a project that runs on Android, iOS, and the web.

## Join the community

Join our community of developers creating universal apps.

- [Expo on GitHub](https://github.com/expo/expo): View our open source platform and contribute.
- [Discord community](https://chat.expo.dev): Chat with Expo users and ask questions.
