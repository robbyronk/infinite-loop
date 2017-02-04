    A generator is a special function that can pause, return out a value and pick up where it left off later with another input
    A generator can be used to code simple workflows.
        Simple because you can't serialize them. 
    Redux Sagas is a library that lets you use generators to code simple workflows to work with a Redux state
        Examples
            Delayed login
            Polling for data changes