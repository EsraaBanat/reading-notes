# Context API - Behaviors

## Snackbars:

```js
const { addAlert } = useSnackBars()
...
addAlert('Your profile is updated!')
```

## Globally Accessible


The state of our snackbars (which ones are visible) can be localized to a single centralized component. That same centralized component can be responsible for rendering them. There’s really no need for another component somewhere in the tree to hook into that state (at least not in our use-case).

However, the management of that state (adding, removing) needs to be globally accessible

```js
export const SnackBarContext = createContext()

export function SnackBarProvider({ children }) {
  const [alerts, setAlerts] = useState([])

  return (
    <SnackBarContext.Provider value={{ setAlerts }}>
      {children}
      {alerts.map((alert) => <SnackBar key={alert}>{alert}</SnackBar>)}
    </SnackBarContext.Provider>
  )
}
```
The other half of the puzzle is we now need a consumer for this provider. It turns out that our custom hook from before is nothing more than a small wrapper around the useContext internal React hook, which consumes our new context.

```js
import { useContext } from 'react'

import { SnackBarContext } from 'components/snack-bar-provider'

const useSnackBars = () => useContext(SnackBarContext)

export default useSnackBars
```

## Higher Level API & Behaviour


```js
export const SnackBarContext = createContext()

const AUTO_DISMISS = 5000

export function SnackBarProvider({ children }) {
  const [alerts, setAlerts] = useState([])
  
  const activeAlertIds = alerts.join(',')
  useEffect(() => {
    if (activeAlertIds.length > 0) {
      const timer = setTimeout(() => setAlerts((alerts) => alerts.slice(0, alerts.length - 1)), AUTO_DISMISS)
      return () => clearTimeout(timer)
    }
  }, [activeAlertIds])

  const addAlert = (alert) => setAlerts((alerts) => [alert, ...alerts])

  const value = { addAlert }
    
  return (
    <SnackBarContext.Provider value={value}>
      {children}
      {alerts.map((alert) => <SnackBar key={alert}>{alert}</SnackBar>)}
    </SnackBarContext.Provider>
  )
}
```

There’s a lot more happening now. Our provider now exposes a new function called `addAlert`. This function uses the local state mutator `useState` to properly append a new alert without destroying existing ones. You could do more fancy things here: de-dup alerts, assign unique IDs to alerts so that we can also expose a `removeAlert` function that makes use of those IDs, and so on. But we’re going to keep it simple.

Most importantly perhaps is that we now make use of `useEffect` to display each alert for 5 seconds on the screen

## Room for Change

There’s a lot of buzz around how you can replace a lot of what Redux does with `useContext` and `useReducer`. The combination of these two hooks means we can have a global state and use Redux-like reducers, actions, and dispatchers to mutate that global state. To an extent, it’s possible.

# References

## [Hooks and Context example](https://reactjs.org/docs/context.html)

## [Awesome React Context links](https://github.com/diegohaz/awesome-react-context)

## [Back To Home Page](../../README.md)
