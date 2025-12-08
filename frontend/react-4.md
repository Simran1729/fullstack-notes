## Common Hooks and Custom Hooks

1. Two jargons:

- Side Effects
- Hooks

In react, side effects encompasses any opearation that reach outside the functional scope of a React componet, these operatin can affect other component, interact with the browser, or fetch data.
Bascially anything in your component not related to ui lifeccucle of adding / remvoing / updating

2. So these need to be seperate from our rendering.

3. Hooks are a feature introduced in React 16.8 that allows you to use state and other React features without writin class. Led to more concise and readable way of writing React components.

4. useMemo - hooks that memoized an expensive operation : Whatever you are using inside useMemo function calculation, make sure to pass it in the dependency array:
   const [sentences, setSentences] = useState(ALL_WORDS);
   const [filter, setFilter] = useState("");

   const filteredSentences = useMemo(() => {
   console.log("calling filter")
   return sentences.filter(x => x.includes(filter))}
   ,[filter, sentences])

   otherwise it created inconsistencies in the result, liek filters change - store result and no filter change, no result change, but if senetnecnes change and filter not, but react doesnt re calculate, you see old result - inconsistency

let count = useMemo (() => {
//first arg is function returns something that goes in let count
}, [dependency state variable just like useEffect])

5. useCallback - a hook that memoizes functions, helpful to optimize the performance and prevent re renders especially when child components depend on referntial equality. since functions use refernce to compaure ( not a primite value in js but a refernce values)

let myFunc = useCallback(() => {
// funciton logic
console.log("Hi there")
}, [//dependency when the function should be recomputed, can be left empty])

6. Custom Hooks

#### Consider THIS --> memo and useMemo are different

7. useRef Hook : Lets you acces DOM elements and persist values that should persist between rendres
