### DOM

1. DOM is how broswers allow JS to interact with a rendering engine of the broswer, like (Blink or webkit etc.)

2. That is why it is called DOM provides APIs for DOM manipulation

3. It is hard to build dynamic pages - that is once the page has loaded, it is hard to add dynamic or add more things to the DOM once it has loaded.

4. And that is what in the lond run React makes it easy for you.

5. "document" is a global variable using which you can populate the DOM

6. When you do console.log(document.getElementbyId("firstContainer)); you see something like <div id="firstContainer"></div>, if you check its type it is not html or text, but a DOM object and just like other objects, it provides you various properites and methods to call, so that is why you can call severl methods on it to manipulate it.

7. So if you do this : const element = document.getElementbyId("firstContainer), you can call element.innerHTML = "hello world" , this will manipualte the DOM and hence you see changes on DOM.

### Debounce:

1. When you wait for the user for them to complete the input for search and then you send the request to the backend

2. Or delayed sending out of request or also called throttling

3. So this is the logic, you write a function populateDiv(), on acutal onClikc you call \*\*debouncedPopulateDiv()
   let timeout;
   function debouncedPopulateDiv(){
   clearTimeout(timeout);
   timout = setTimout(() => {
   popualteDiv()
   }, 1000);
   }
   So you write if the debouncedPopulateDiv hasn't been called, you call it and it waits for 1 second to call your populateDiv() and if it already has been called in the same 1 second, you clear that timeout and create a newTimeout for a new request, repeat this and you got yourself a debouncedfunction.

#### React - Reconcilers

1. Making dynaimc websites, with the primitives that DOM provides you is very hard, like document.createElement, .appendChild, setAttribute, element.children

2. It is quite hard to write dom manipulation using given DOM apis like the above, and also because it doesn't have any central state

3. Now let say you have addTodo function but whenver the site reloads the set of todos changes. So one way to render this dynamic todos coming from somewhere is to first, clear the exisitng DOM for that container and then call your createChi ld function or add Todo function to pass that todos in that function to add these Todo on screen.
   So, we need something that will handle this State + Login part and that is where React comes in the picture.

4. But there are few flaws in this approach :

- first we are clearing the DOM, then it adds more things. Lets say backend is sendin you same data and you are still doing the same thing.

5. Better approach is - calculate the diff anytime the state changes.

6. Dont add new thing or alter things, just calculate based on diff, what needs to be changed and what needs to be updated, etc

7. What is the best way to write a dynamic frontend website?

- Update a state variable
- delete the task of figuring out diff to a hefty function
- tell the hefty function to add, update and remove elements.
- so mostly the crux or the work of the React is to updateState(oldState) => { new state }

8.  So basiaclly -

- React - basically just calculates diff
- React DOM - tells React that this is how you put things on the DOM and this how you remove things from the DOM
- React Native - tells react that this is how you put things on a native application and remove and so on

9. ### important! Why keys?
   Keys help React identify which list item is which between renders.

❌ If you use bad keys (like array index):
Problems:

Inputs break

Removing first item shifts indexes →
React reuses wrong DOM nodes →
input focus jumps / values swap.

Component state moves to wrong item

Example: checkbox/timer/dropdown of Todo #1 moves into Todo #2.

Animations glitch

React thinks old item = new item → animations don’t run correctly.

Performance becomes poor

React updates many nodes unnecessarily.

✅ If you use correct keys (unique stable id):
React correctly:

keeps same items

updates only changed items

removes only removed items

keeps input focus + state stable

improves performance

Example:
Good:

<li key={todo.id}>{todo.text}</li>

⭐ Final in one line
Keys prevent React from confusing list items; wrong keys cause UI bugs, lost focus, wrong state, and slow updates.

Refer this url : https://chatgpt.com/c/691a0e2d-0530-8324-b1a9-13b0aa0359d5

10. 1. Dev Mode (Vite)

- Browser loads ES modules directly (multiple small files)
- No bundling
- Uses esbuild (super fast)
- HMR updates only changed modules
- State is preserved, instant updates

2. Production Build

- Browser is slow with hundreds of small files
- Need bundling → merge code into few files
- Tree-shaking removes unused code
- Minifying shrinks size
- Code-splitting loads pages lazily
- Assets are optimized

3. Why Rollup?

- Best tree-shaking
- Converts all modules to optimized bundles
- Used only for final build (not dev)

4. HMR (Hot Module Replacement)

- Replaces only changed modules in real-time
- No full page reload
- App state preserved
- Fast feedback loop

10. React requires component names to start with a capital letter because:

1. JSX treats lowercase tags as HTML elements (div, span, button).
1. Uppercase tags get compiled into React.createElement(Component).
1. Lowercase names get compiled into strings: React.createElement("todo"),
   which creates a custom HTML tag instead of calling the component.
1. Without capitalization, React will never run your component function.

1. Folder Structure:
   everything related to that specific feature.

src/
├── features/
│ ├── auth/
│ │ ├── components/
│ │ │ ├── LoginForm.tsx
│ │ │ └── RegisterForm.tsx
│ │ ├── hooks/
│ │ │ └── useAuth.ts
│ │ ├── services/
│ │ │ └── authAPI.ts
│ │ ├── store/
│ │ │ └── authStore.ts
│ │ ├── types/
│ │ │ └── authType.ts
│ │ └── index.tsx
│ ├── dashboard/
│ ├── settings/
│ └── ...
├── shared/
│ ├── components/
│ │ ├── Button.tsx
│ │ └── Input.tsx
│ ├── hooks/
│ ├── store/
│ ├── types/
│ └── utils/
