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

## Contact Form with Validation

```js
import React, { useState, useEffect } from "react";

const RegisterForm = () => {
  const validateForm = () => {
    const tabs = document.getElementsByClassName("tab");
    const inputs = tabs[currentTab].getElementsByTagName("input");
    let valid = true;

    // Clear all existing error messages
    const errorMessages = document.getElementsByClassName("error-message");
    for (let i = 0; i < errorMessages.length; i++) {
      errorMessages[i].innerText = "";
    }

    // Validate each input field
    for (let i = 0; i < inputs.length; i++) {
      const fieldName = inputs[i].getAttribute("name");
      const errorElement = document.getElementById(`${fieldName}-error`);
      if (inputs[i].value === "") {
        if (errorElement) {
          errorElement.innerText = "This field is required.";
        }
        inputs[i].classList.add("invalid-field"); // Apply invalid-field class
        valid = false;
      } else if (errorElement) {
        errorElement.innerText = ""; // Clear error message if field is not empty and error element exists
        inputs[i].classList.remove("invalid-field"); // Remove invalid-field class
      }
    }

    // Hide the error message if the form is valid
    if (valid) {
      const errorMessage = document.getElementById("errorMessage");
      errorMessage.style.display = "none";
    }

    return valid;
  };

  const patterns = {
    username: /^[a-z\d]{5,12}$/i,
    dni: /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/,
  };

  useEffect(() => {
    const inputs = document.querySelectorAll("input");

    // attach keyup events to inputs
    inputs.forEach((input) => {
      input.addEventListener("keyup", (e) => {
        validate(e.target, patterns[e.target.attributes.name.value]);
      });
    });
  }, []);

  // validation function
  function validate(field, regex) {
    if (regex.test(field.value)) {
      field.className = "valid";
    } else {
      field.className = "invalid";
    }
  }

  return (
    <>
      <div></div>
      <form id="regForm" action="/action_page.php">
        <div className="tab">
          <input
            type="text"
            name="username"
            placeholder="username"
            className=" block px-8 py-4  mx-auto my-8 w-full box-border rounded-lg border-2 border-[#ccc] outline-none"
          />

          <p>Username must be and contain 5 - 12 characters</p>

          <input
            type="password"
            name="dni"
            placeholder="Password"
            className=" form_input block px-8 py-4  mx-auto my-8 w-full box-border rounded-lg border-2  border-[#ccc] outline-none"
          />
          <p>
            Minimum eight characters, at least one uppercase letter, one
            lowercase letter, one number and one special character:
          </p>
        </div>
      </form>
    </>
  );
};

export default RegisterForm;



//  CSS

.tab input{
  background-color: transparent;
  color: black;
  display: block;
  padding: 8px 16px;
  font-size: 2em;
  margin: 10px auto;
  width: 100%;
  box-sizing: border-box;
  border-radius: 10px;
  border: 3px solid #ccc;
  outline: none !important;
}

/* validation styles */

input.valid{
  border-color:rgb(51, 255, 0);
}

input.invalid{
  border-color: red;
}

input + p{
  font-family: arial;
  font-size: 0.9em;
  font-weight: bold;
  text-align: center;
  margin: 0 10px;
  color: orange;
  opacity: 0;
  height: 0;
}

input.invalid + p{
  opacity: 1;
  height: auto;
  margin-bottom: 20px;
}

#errorMessage{
  color: red;
  display: none;
}
```


## Responsive Container CSS

```
.header_container {
    @media (min-width: 576px) {
        max-width: 540px;
    }
    @media (min-width: 768px) {
        max-width: 720px;
    }
    @media (min-width: 992px) {
        max-width: 960px;
    }
    @media (min-width: 1200px) {
        max-width: 1140px;
    }
    @media (min-width: 1400px) {
        max-width: 1320px;
    }
    @media (min-width: 1500px) {
        max-width: 1440px;
    }
    @media (min-width: 1600px) {
      max-width: 1680px;
    }
    width: 100%;
    padding-right: 0.75rem;
    padding-left: 0.75rem;
    margin-right: auto;
    margin-left: auto;
    padding-top: 15px;
    padding-bottom: 15px;
  }
```
