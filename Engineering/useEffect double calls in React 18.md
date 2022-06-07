---
tags: engineering, react 18, react hooks, useEffect
author: T.Hoang Nam (Nigel)
---

### useEffect double calls in React 18

In the React 18 version, the useEffect hook has been updated to called twice compare to only one in the older version in StrictMode.

**What are the changes and why?**
- Beginning with React 18, when in development mode, the components will be mounted, unmounted, and then mounted once again in StrictMode.
- This was introduced so that in the future, when React decides to offer a feature that allows it to add or delete an area of the UI while still maintaining the state, this will help it do so. For instance, when moving between tabs, maintaining the state of the preceding tab might assist avoid the execution of effects such as API calls that are not essential.

**What are the differents?**

- In React 17 the useEffect hook gets call every time the component is mounted.
- In React 18 each component is mounted, then unmounted, and then remounted and an useEffect call with no dependencies will be run double-time in strict mode.

### Example of useEffect in React 18
We can confirm the behavior by using the cleanup function of the useEffect hook.
```
useEffect(() => {
  console.log("Hello Dwarves!");
  return () => console.log("Cleanup..");
}, []);
```
The output to the console should look like this:
```
Hello Dwarves!
Cleanup..
Hello Dwarves!
```

**Solution**
- Embrace the double-firing and make sure your clean up function works (so double-firing in development doesn't hurt).

**Get around (not recomended)**
- You can create a custom hook so that the useEffect get called only once, although this approach can cause leaks and overall not the best practice in engineering.

```
export const useEffectOnce = (effect: () => void | (() => void)) => {
  const destroyFunc = useRef<void | (() => void)>();
  const effectCalled = useRef(false);
  const renderAfterCalled = useRef(false);
  const [val, setVal] = useState<number>(0);

  if (effectCalled.current) {
    renderAfterCalled.current = true;
  }

  useEffect(() => {
    // only execute the effect first time around
    if (!effectCalled.current) {
      destroyFunc.current = effect();
      effectCalled.current = true;
    }

    // this forces one render after the effect is run
    setVal((val) => val + 1);

    return () => {
      // if the comp didn't render since the useEffect was called,
      // we know it's the dummy React cycle
      if (!renderAfterCalled.current) {
        return;
      }
      if (destroyFunc.current) {
        destroyFunc.current();
      }
    };
  }, []);
};
```

#### Reference

- https://www.techiediaries.com/react-18-useeffect/
- https://dev.to/ag-grid/react-18-avoiding-use-effect-getting-called-twice-4i9e
