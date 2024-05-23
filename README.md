# NextJs

## Input Type Number allowed e,E,+,-,* 
- " <input type="number" onKeyDown={(e) =>["e", "E", "+", "-"].includes(e.key) && e.preventDefault()} /> "
- oninput="validity.valid||(value='');
  


## Dark Mode Implementation 
- **Step - 1 Add Darkmode selector in tailwind.config.js**
  
```js
module.exports = {
  darkMode: 'selector',
  // ...
}
```
- **Step - 2 Add Dark Mode Function.**
```js
const [darkMode, setDarkmode] = useState(false);

  const toggledarkmode = () => {
    setDarkmode(!darkMode);
  }
  ```
- **Step - 3 Add Class in Main HTML.**
```js
 <html lang="en" className={`${darkMode && "dark"}`} >
```

- **Step - 4 Pass parameters to toggle button section.**
```js
 <Header darkMode={darkMode} toggledarkmode={toggledarkmode} />
```

- **Step - 5 Get Props in Header so that toggle button can use it.**

```js
const Header = ({ darkMode, toggledarkmode }) => {
            //Your Other Code
};
```

- **Step - 6 Add a Dark Mode Toggle Button.**
```js
<button onClick={toggledarkmode} className='hover:scale-110 sm:m-4'>
        {darkMode ?
          <svg className="flex-shrink-0 size-4 dark:dark:text-gray-200 " xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
            <circle cx="12" cy="12" r="4"></circle>
            <path d="M12 2v2"></path>
            <path d="M12 20v2"></path>
            <path d="m4.93 4.93 1.41 1.41"></path>
            <path d="m17.66 17.66 1.41 1.41"></path>
            <path d="M2 12h2"></path>
            <path d="M20 12h2"></path>
            <path d="m6.34 17.66-1.41 1.41"></path>
            <path d="m19.07 4.93-1.41 1.41"></path>
          </svg>
          :
          <svg className="flex-shrink-0 size-4 " xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round">
            <path d="M12 3a6 6 0 0 0 9 9 9 9 0 1 1-9-9Z"></path>
          </svg>
        }
      </button>
```
- **Step - 7 Add a Dark Class wherever needed.**
```js
<header className="bg-white dark:bg-[#666666]">
```
