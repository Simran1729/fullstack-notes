### React Routing, Prop Drilling and Context API

1. Jargon to Know : SPA, Client Side Bundle , Client Side Routing

- SPA : SPA is a single page application which is what most of the frameworks create today , like a single index.html which just updates the DOM
- Client Side Bundle : Its a bundle of files containing - html, css and js that is sent by the server when the app reloads and contains the entire code our frontend app.
- Client Side Routing : Its the code that we write in our frontned app, like this is what should be rendered on this route and so on.

# Syntax : Using react-router-dom (most popular library used for react routing in a web app)

2. App returns (
   <BroswerRouter>
   <Routes>
   <Route path = "/dashboard" element={<Dashboard/>} >
   </Routes>
   </BroswerRouter>
   )
   So, this Broswer Router is like a wrapper component if you remeber like passing {children}

dont do this: <div style={{color: "red", background: "pink", padding: "8px 0 8px 8px"}}>
This is header
<a href="/dashboard">Dashboard</a>
<a href="/">Home</a>

</div>

it will just cause http request to your server to get html again- so it beats the purpose of using react router dom, instead use
useNavigate () hook

3. Make sure Link is inside your BrowswerRouter component since it needs context and soem goes for useNavigate - should be used in component which is a children of BroswerRouter

3.5. ==> Link vs useNavigate subtle use case differnce:
Link is used where you specifically want the user to click and navigates to some page
useNavigate - ko tum khud bhi navigate krva skte ho user ko

## LazY Loading :

4. Now when the application loads the first time, it gives the bundle containing entire code of the app, but we dont want that we want that whenver user goes to the desired page, it only is fetched then - This is called Lazy Loading

# syntax:

const Dashboard = React.lazy(() => import("./pages/Dashboard"))

!! Make sure the export is deafult for a component to lazy load

!! Make sure to add Suspense api in lazy loading it keeps a fallback while the component is fetched asynchronously

### Prop Drilling :

5. Drilling down the props from to components whihc dont really need the prop to pass it to the components which actually need them.

# Its an anti pattern

6. useReducer is also a great thing. Try to read about it.
