---
title: "Creating forms in React"
datePublished: Wed Aug 23 2023 21:51:42 GMT+0000 (Coordinated Universal Time)
cuid: cllo9scfa000009iacc339gy5
slug: creating-forms-in-react
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692830269374/b4b6de8e-8798-49ce-9cf7-3039233eb3b3.jpeg
tags: javascript, reactjs, reacthooks, react-forms

---

### Introduction

Forms are essential components of the web, whether created with just HTML or with frameworks like React. Forms allow users to send data, perform basic tasks on the internet such as posting a tweet, sending a message, or online shopping, and also retrieve data. Forms are the web's foundation, and networking would not be possible without them.

Creating effectual forms is a necessity for developers because it allows them to collect data from users in a way that is efficient and easy to understand. When forms are well-designed, they can help developers avoid errors and ensure they are collecting the data they need. Additionally, effective forms can help improve the user experience by making it easy for users to provide the needed information.

Unlike HTML forms, React allows for the dynamic handling of form data. When working with forms in HTML or vanilla Javascript, it's essential to remember that the inputs can only be processed after submitting the form. This means that any changes made by the user won't be monitored until the very end of the process. However, in React, we have the ability to create states that can track every change made during the user's interaction with the form. This is a powerful tool that can significantly improve the user experience and make the process much more efficient. Information processing starts as soon as the user begins interacting with the form. This means that after submitting the form, we submit the data and pass the state that we have been tracking all along.

React presents two ways to handle data in forms: The first way is through uncontrolled components, which allow the form elements and data to be handled by the DOM. The second way is through controlled components, where the data is fully handled by React through hooks.

## Prerequisites

* Proficiency in HTML, particularly HTML forms and form elements, and CSS.
    
* Knowledge of Javascript
    
* Knowledge of the DOM
    
* Basic knowledge of React and useState hook
    
* A text editor for writing code
    

## Creating Forms Through Uncontrolled Components

In uncontrolled components, the state of form elements is not managed by React, but rather by the DOM. When users input text into form fields in uncontrolled components, the browser controls the state of those elements and updates the DOM for that element.

Here, no value property is set for form elements, instead, we use the `onChange` event handler to receive users' input. Moving on in this tutorial, we will:

* Create basic forms
    
* Manage the state of our input with the `useState` hook
    

### Creating Simple Forms

First, create a <mark>Form.js</mark> file and import `react` and `useState`

```javascript
import React, { useState } from "react"
```

Then, export a default `Form` function, returning a `form` element within it

```javascript
export default function Form () {
    return (
        <form>

        </form>
    )
}
```

Then, create an `input` element inside the form with a type and placeholder of `First name` and an `onChange` event while passing in a `handleChange` function. Like below

```javascript
import React, { useState } from "react"

export default function Form () {
    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
        </form>
    )
}
```

So, let's handle changes in the `First name` input using the `useState` hook. Let’s just create a `handleChange` function and `console.log` to check for changes in our input.

The `handleChange` function must be nested inside the form component like below

```javascript
import React, { useState } from "react"

export default function Form () {

    function handleChange() {
        console.log("Changed!")
    }

    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
        </form>
    )
}
```

So, we can test and see that as we type into our input field, Changed! is printed to the console

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692798031375/b44dc77b-aa8d-4dec-8d68-22bea4e0bec5.gif align="center")

Next, we use let to declare a `firstName` variable and `console.log` `firstName` to see the changes in the user’s input as they type

```javascript
import React, { useState } from "react"

export default function Form () {

    let firstName

    console.log(firstName)


    function handleChange() {
        console.log("Changed!")
    }

    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
        </form>
    )
}
```

In our `onClick` handler function, we pass `event` to our function, then we remove the `console.log` there, replacing it with the code

```javascript
function handleChange(event) {
        firstName = event.target.value
    }
```

The code would appear as follows

```javascript
import React, { useState } from "react"

export default function Form () {

    let firstName

    console.log(firstName)


    function handleChange(event) {
        firstName = event.target.value
    }

    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
        </form>
    )
}
```

Let's execute the file and see the output in the console

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692798495893/d8d74211-0a6c-4190-8b55-ddb566a09978.gif align="center")

We can see that despite typing repeatedly, nothing happens in our console because React cannot detect changes in `firstName`, so we use the `useState` hook to declare our variable and set a state to allow for changes in `firstName`.

First, we declare an array of `firstName` and `setFirstName` equal to `useState` which is set to an empty string

```javascript
    const [firstName, setFirstName] = useState("")
```

Next, we pass an event object from the `onClick` event handler to our `handleClick` function, and then we replace the `console.log` to update the `firstName` state on every keystroke

```javascript
function handleChange(event) {
        setFirstName(event.target.value)
    }
```

Then add a console.log in the body of the Form function to see the changes in user input as they type

```javascript
import React, { useState } from "react"

export default function Form () {

    const [firstName, setFirstName] = useState("")

    console.log(firstName)


    function handleChange(event) {
        setFirstName(event.target.value)
    }

    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
        </form>
    )
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692798845591/a847809b-3f84-40d6-9cf3-2a7411f04abf.gif align="center")

We can see that, unlike the previous attempt, React is able to detect changes in its input and update `firstName` accordingly.

## Adding another input field to the form

We can add another input field to the form in two ways and we’ll explore both ways in this section

### A. Duplicating Our Former Code By Adding Another Hook

By duplicating our former code and editing it accurately, we can add another `input` field, and track and update its state in React as we formerly did.

First, we create another `input` field with an `onChange` event listener with a `handleSurName` function

```javascript
<input type="text" placeholder="surName" onchange={handleSurName} />
```

We create our `surName` state variable with the `useState` hook

```javascript
    const [surName, setSurName] = useState("")
```

The next step is to create the `handleSurName` function using the `handleChange` function as a model

```javascript
import React, { useState } from "react"

export default function Form () {

    const [firstName, setFirstName] = useState("")
    const [surName, setSurName] = useState("")


    function handleChange(event) {
        setFirstName(event.target.value)
    }

    function handleSurName(event) {
        setSurName(event.target.value)
    }


    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
            <input type="text" placeholder="surName" onchange={handleSurName} />

        </form>
    )
}
```

Then console.log the `firstName` and `surName` to allow us to see the output

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692799933153/7a068a9c-8216-4f26-b6de-4d683a7354aa.gif align="center")

However, if we have more inputs, we will duplicate more code, leading to poor-quality code that may make it difficult to maintain. In the next section, we will learn how to do the same thing in a cleaner and more acceptable format.

### B. Combining State into Object

By combining states, we can create and maintain a single state to manage multiple inputs. This allows us to use a single state to control and manage multiple inputs, checkboxes, and radio elements. It gives us greater control, simplifies the code, and improves code quality, especially if the code is to be used by other developers.

First, we the duplicate `handleSurName` and state variable and replace the placeholder `surName` with `lastName` since that's easily understandable, and we pass `handleChange` to it

```javascript
import React, { useState } from "react"

export default function Form () {

    const [firstName, setFirstName] = useState("")


    function handleChange(event) {
    }


    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
            <input type="text" placeholder="lastName" onchange={handleChange} />

        </form>
    )
}
```

To create a single state that can be used by all types of input, we need to create an object in the state. A state variable can accept multiple data types, so we create the object in the state. We need to change the name of the variable from `firstName` to something more generic, like `formFields`

```javascript
import React, { useState } from "react"

export default function Form () {

    const [formFields, setFormFields] = useState({
        firstName: "",
        lastName: ""
    })


    function handleChange(event) {
    }


    return (
        <form>
            <input type="text" placeholder="First Name" onChange={handleChange} />
            <input type="text" placeholder="lastName" onchange={handleChange} />

        </form>
    )
}
```

Unfortunately, we cannot use `event.target.value` to get the data from the form fields because rather than giving us our data in object form, our object will be erased and the output will be a string, which is not helpful. Since we are using the same `handleChange` function on both inputs, we need a way to identify which input triggered the event. To do this, we give the inputs a `name` property that matches the property name that we are storing

```javascript
       

          <input 
                type="text" 
                placeholder="First Name" 
                onChange={handleChange} 
                name="firstName" 
                />

            <input 
                type="text" 
                placeholder="Last Name" 
                onChange={handleChange} 
                name="lastName" 
                />
```

To check if our code is working, we’ll `console.log` `event.target.name` to check which input field is triggering the event listener. Let’s test our code

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692800989990/08ad37b1-86e0-4259-896d-5b2fecd95711.gif align="center")

With this, we have everything we need to call `formFields` and update our object correctly. To do this, we call `setFormFields` to accept changes in state and update our `formFields` variable respectively. We’ll call `setFormFields` in our `onChange` function, and then we’ll pass our previous state (we didn’t do that with strings because overwriting our file doesn’t actually change anything) preventing outright overwriting of our earlier state, passing a callback function which will then return an object. The object takes in a copy of the previous state, then the specific property we want to change in the object is passed to it. This causes only the value of the property we want to change to be overwritten whilst preserving the other components of the object

```javascript
import React, { useState } from "react"

export default function Form () {

    const [formFields, setFormFields] = useState({
        firstName: "",
        lastName: ""
    })

    function handleChange(event) {
        setFormFields(prevState => {
            return {
                ...prevState,
                [event.target.name]: event.target.value
            }
        })
    }

    return (
        <form>
            <input 
                type="text" 
                placeholder="First Name" 
                onChange={handleChange} 
                name="firstName" 
                />

            <input 
                type="text" 
                placeholder="Last Name" 
                onChange={handleChange} 
                name="lastName" 
                />
        </form>
    )
}
```

Computed properties was used to turn the dynamic string `event.target.name` and use it as the property name for the object. `Console.log` `formFields` to see our state as it changes

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692801583991/c459513e-2dde-4665-9cee-ef04a7b40e9f.gif align="center")

The object is initially empty but as we start typing, the object starts changing and our state remains intact.

### Adding Another Input

Adding another input field will be very easy since we just have to add a new field to our state object rather than adding another event handler function and a new state.

Let’s demonstrate that by adding a **Username** field in our state object. Kindly ensure that the name of the property in the state object is the same as the one in the input tag

```javascript
import React, { useState } from "react"

export default function Form () {

    const [formFields, setFormFields] = useState({
        firstName: "",
        lastName: "",
        userName: ""
    })


    function handleChange(event) {
        setFormFields(prevState => {
            return {
                ...prevState,
                [event.target.name]: event.target.value
            }
        })
    }


    return (
        <form>
            <input 
                type="text" 
                placeholder="First Name" 
                onChange={handleChange} 
                name="firstName" 
                />

            <input 
                type="text" 
                placeholder="Last Name" 
                onChange={handleChange} 
                name="lastName" 
                />

            <input 
                type="text" 
            	placeholder="Username" 
            	onChange={handleChange} 
           		name="userName" 
          		/>

        </form>
    )
}
```

Let’s add `favColour` to the state object

```javascript
const [formFields, setFormFields] = useState({
        firstName: "",
        lastName: "",
        userName: "",
        description: "",
        isTrue: true,
        tiers: "",
        favColour: ""
    })
```

Then, we add a `name`, `value` and the `onChange` event handler to the `select` element

```javascript
<select 
                    id="favColour"
                    name="favColour"
                    value={formFields.favColour}
                    onChange={handleChange}
                    >
```

With those lines of code, the dropdown works as expected

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692821632126/90085bd3-e3d8-409e-a4c5-de1856ab5cb2.gif align="center")

However, the initial value of the `select` element is an empty string, but there is no option that represents the empty string. We can resolve that by creating an option element with an empty string value

```javascript
<option value="">-- Choose --</option>
```

And this is the total code

```javascript
import React, { useState } from "react"

export default function Form () {

    const [formFields, setFormFields] = useState({
        firstName: "",
        lastName: "",
        userName: "",
        description: "",
        isTrue: true,
        tiers: "",
        favColour: ""
    })


    function handleChange(event) {
        const {name, value, type, checked} = event.target
        setFormFields(prevState => {
            return {
                ...prevState,
                [name]: type === "checkbox" ? checked : value
            }
        })

    }


    return (
        <form>
            <input 
                type="text" 
                placeholder="First Name" 
                onChange={handleChange} 
                name="firstName" 
                value={formFields.firstName}
                />

            <input 
                type="text" 
                placeholder="Last Name" 
                onChange={handleChange} 
                name="lastName" 
                value={formFields.lastName}
                />

            <input 
                type="text" 
                placeholder="Username" 
                onChange={handleChange} 
                name="userName" 
                value={formFields.userName}
                />

            <textarea 
                placeholder="description"
                onChange={handleChange}
                name="description"
                value={formFields.description}
                />

            <input
                type="checkbox"
                id="isTrue"
                checked={formFields.isTrue}
                onChange={handleChange}
                name="isTrue"
                    />
                <label htmlFor="isTrue">Subscribing</label>
              
                <select 
                    id="favColour"
                    name="favColour"
                    value={formFields.favColour}
                    onChange={handleChange}
                    >
                    <option value="">-- Choose --</option>
                    <option value="red">Red</option>
                    <option value="blue">Blue</option>
                    <option value="yellow">Yellow</option>
                    <option value="indigo">Indigo</option>
                    <option value="orange">Orange</option>
                    <option value="violet">Violet</option>

                </select>

        </form>
    )
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692821790022/54246614-85dd-406d-918e-5e601ba8e623.gif align="center")

## Submitting Forms

In React, the `button` element is used to handle the submit. By default the button element is of type `submit`, so we’ll use this in our code

```javascript
<button>Submit</button>
```

Clicking the button will cause the form to trigger the `onSubmit` event handler. So, we add the `onSubmit` event handler prop to our form with the `handleSubmit` function which we’ll create

```javascript
<form onSubmit={handleSubmit}>
```

Next, create the `handleSubmit`  function and pass the `event` to it. In the body of the function, run `event.preventDefault` to prevent the page from refreshing, causing React to rerender the component

```javascript
function handleSubmit(event) {
        event.preventDefault()
    }
```

This is the whole code, you can style it way you want to

```javascript
import React, { useState } from "react"



export default function Form () {
    const [formFields, setFormFields] = useState({
        firstName: "",
        lastName: "",
        userName: "",
        description: "",
        isTrue: true,
        tiers: "",
        favColour: ""
    })


    function handleChange(event) {
        const {name, value, type, checked} = event.target
        setFormFields(prevState => {
            return {
                ...prevState,
                [name]: type === "checkbox" ? checked : value
            }
        })
    }

    function handleSubmit(event) {
        event.preventDefault()
    }

    return (
        <form onSubmit={handleSubmit}>
            <input type="text" 
            placeholder="First Name" 
            onChange={handleChange} 
            name="firstName" 
            value={formFields.firstName}
            />

            <input type="text" 
            placeholder="Last Name" 
            onChange={handleChange} 
            name="lastName" 
            value={formFields.lastName}
            />

            <input type="text" 
            placeholder="Username" 
            onChange={handleChange} 
            name="userName" 
            value={formFields.userName}
            />

            <textarea 
                placeholder="description"
                onChange={handleChange}
                name="description"
                value={formFields.description}
                />

              <input
                    type="checkbox"
                    id="isTrue"
                    checked={formFields.isTrue}
                    onChange={handleChange}
                    name="isTrue"
                    />
                <label htmlFor="isTrue">Subscribing</label>
                <br />
         

                <fieldset>

                    <legend>Choose Subscription Plan</legend>

                    <input 
                        type="radio"
                        id="tier1"
                        name="tiers"
                        value="tier1"
                        onChange={handleChange}
                        checked={formFields.tiers === "tier1"}
                    />
                    <label htmlFor="tier1">Tier 1</label>
                    <br />
                    <input 
                        type="radio"
                        id="tier2"
                        name="tiers"
                        value="tier2"
                        onChange={handleChange}
                        checked={formFields.tiers === "tier2"}
                    />
                    <label htmlFor="tier2">Tier 2</label>
                    <br />
                    <input 
                        type="radio"
                        id="tier3"
                        name="tiers"
                        value="tier3"
                        onChange={handleChange}
                        checked={formFields.tiers === "tier3"}
                    />
                    <label htmlFor="tier3">Tier 3</label>
                    <br />
                </fieldset>
                <br />

                <label htmlFor="favColour">What is your favourite colour</label>
                <br />

                <select 
                    id="favColour"
                    name="favColour"
                    value={formFields.favColour}
                    onChange={handleChange}
                    >
                    <option value="">-- Choose --</option>
                    <option value="red">Red</option>
                    <option value="blue">Blue</option>
                    <option value="yellow">Yellow</option>
                    <option value="indigo">Indigo</option>
                    <option value="orange">Orange</option>
                    <option value="violet">Violet</option>

                </select>
                <br />
                <br />

                <button>Submit</button>

        </form>
    )
}
```

With that, we’ve come to the end of this how-to guide.

## Conclusion

Congratulations! You can now create forms in React. To access the source code used in this tutorial, head over to the [repository](https://github.com/joshua094/ReactForms-tutorial) to get it.