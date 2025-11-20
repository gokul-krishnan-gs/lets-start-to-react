## Redux
Redux is a state management library used to store and manage global data in one centralized place.
Instead of keeping state inside many components, Redux keeps everything in a global store so the app becomes clean and predictable.

In Redux Toolkit, we create slices.
Each slice has a name, initial state, and reducers (the actual logic that updates the state).

Components use a dispatcher to trigger an action, and reducers decide how the state should change.

The slice reducers are combined into a store, and the entire React app is wrapped in a Provider so every component can access Redux state.

