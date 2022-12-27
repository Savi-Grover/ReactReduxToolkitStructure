Step 1- Basic React project setup

Step 2- npm install @reduxjs/toolkit react-redux

Step 3- Create a Folder app and file inside - store.js with: 

                    import {configureStore } from "@reduxjs/toolkit";
                    export const store=configureStore({
                        reducer:{
                              }
                              
Step 4- Now inside src- make a new folder- features > counter- file> counterSlice.js with code declaration - initial state; reducer [ redux logic ]

                      import { createSlice } from "@reduxjs/toolkit";
                      const initialState={

                          count: 0
                      }

                      export const counterSlice=createSlice({
                      name: 'counter',
                      initialState,
                      reducers: {
                          increment : (state)=>{
                              state.count+= 1;
                          },
                          decrement : (state)=>{
                              state.count-=1;
                          }
                      }


                      })

                      export const {increment, decrement} = counterSlice.actions;
                      export default counterSlice.reducer;
                      
 Step 5 - Now make a counter.js in counter folder: ( for react UI )

                import {useSelector, useDispatch} from "react-redux";
                import {increment, decrement} from './CounterSlice';
                const Counter = () => {
                    const count = useSelector((state) => state.counter.count);
                    const dispatch = useDispatch();
                    return (  
                        <section>
                        <p>{ count }</p>
                            <div>
                                <button onClick={()=> dispatch(increment())}>+</button>
                                <button onClick={()=> dispatch(decrement())}>-</button>
                            </div>

                        </section>

                    )
                }

                export default Counter;
                
Step 6- Go to store.js - to note Reducer info
            import {configureStore } from "@reduxjs/toolkit";
            import counterReducer from '../features/counter/CounterSlice';

            export const store=configureStore({
                reducer:{
                    counter: counterReducer  //use , if more reducers
                }
            })

Step 7 - put as component in App.js

          import Counter from "./features/counter/Counter";
          function App() {
            return (
              <div className="App">
                < Counter />
              </div>
            );
          }
          export default App;
          
Step 8 - Git build /deploy -

  https://savi-grover.github.io/ReactReduxToolkitStructure/


