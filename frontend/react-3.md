## React Returns, re renders, what does React returns, keys, some common Hooks

# React component Returns

1. You can never return multiple siblings like
   return (
      <div>child1</div>
      <div>child2</div>
      )

   The above is wrong
   Reason : It makes reconcilation easy for react, basic reason is this.
   So you either just add extra level <div> or empty tag <> </> or this <React.Fragment> </React.Fragment>

2.A re-render means that

- React did some work to calculate what all should update in this component
- The component actually got callled ( you can put a log to confirm this)
- The inspector shows you a bounding box around the component (inside reactdev tools in inspect)

It happens when

- A state variable that is being used inside a component changes
- A parent component re-render trigger all children re-rendering

But you want to minimize the re-renders, the less re-renders the better/optimized the application is

3.  One way is to push the state down to child if that child is using it and not to use it in parent

4.  Now the rule of the thumb is :
    "he "owner" of the state should be the closest common parent of all components that need it." Because you cannot pass state from children to parent or sibling to sibling ( When I say pass I mean, state defined in child and passed to parent , not possible, but can define it in parent and pass to child and so that two siblings can use it)

5.  Other way to minimize re-renders when the compnonent is not using a state or that state is not being updated or just because parent is re-rendering then it is renderin - > You can use React.memo

6.  Basically React.memo lets you skip re-rendering if the component's props were not changed

7.  Example is :
    <button onClick={change}>Click to change title</button>
    <HeaderComp title={title}/>

             <br></br>
            <HeaderComp title={"simran"}/>

// You just wrap your component inside React.memo function and then assign a name to it, using which the component will be called
const HeaderComp = React.memo(function Header({ title }) {
return (

<div>
{title}
</div>
);
})

8. Never write setTitle() directly inside some handler, this way you are calling it direclty inside function, react doesnt work this way correct syntax is function () { setTitle()}

9. Never push state from child to parent - this is anti pattern

# 10. Keys in React :

When you render a list make sure to give items unique keys, otherwise it becomes harder for React to do reconcilcation. Try not to use random keys using Math.random().
These keys are required by React to uniquely identify items.

11. Wrapper Components: A component which can take other components as input and wrap some logic on it. Liek this :
    <Wrapper>{children}</Wrapper>

# 12. Hooks:

Functions that allow you "hook into" React state and lifecycle features from functional Components. Previously React used class based components and used functions like componentDidMount() and componentDidUnmount() - it became messy and functional components didn't have any of these. So Hooks sovle this problem.

# 13. useEffect Hook:

useEffect(() => {
// logic you write here, work on first mount - componentDidMount()
return () => {
//logic you write here, works when component unMounts - componenetDidUnmount()
// also called clean up function
}
} , [])
