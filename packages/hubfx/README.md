# Motivation:

1. Current UI Library/Frameworks still require us to imperatively manage state

- examples:

  - in react we still use the setter from useState hook

  - in angular many developers still handle state by managing a component class property

- this leaves the door open for implicit depedencies resulting to unexpected side-effects and ultimately unexpected behaviour.

1. application state and business logic is coupled with rendering libraries

- How did we get there?

  - we use to have MVC but then we went the component route

    - good but then we coupled business logic with the view and presentation in component classes/functions

- buisness logic is hard to reuse

- business logic is hard to test without rendering the component

# Proposed solution

- model application state as reactive streams with rxjs allowing us to:

  - decouple application state and business logic from rendering libraries/frameworks

    - we can separate concerns and test our application logic via streams

- state is updated with actions and reducers in the stream and all dependencies are explicit

- this new model can be bound with any UI library for rendering

- CONCLUDED was approaching effects all wrong

- NOW TO REFACTOR using merge all and creating effects dynamically as part of actions

- # 2023 08 01 (Sun)
1. Async validation effects - IN PROGRESS

  - action creator to map argument to proper key/payload/effect action

  - test messages

1. UPDATE reducer for async validation

  - async validation on value update should set validating to true in reducer - IN PROGRESS

  - also valid state on parents and control should be false if it is validating

# TODOS

1. handling adding and removing array items

1. reset form , and set Pristine value


## CLEAN UP TODOS

### FORMS

1. Dynamically adding/removing controls to formGroup?

1. need a way of handling custom actions with the form

- custom reducers/effects to merge with form?

1. SHOULD INITIALIZE and async validate at beginning?

1. better way to copy compare objects than JSON STRINGIFY?


1. update touched action in reducer. handle

- create update touched reducer (state, controlRef)
  - it will be called when user updates value and when user has action TOUCH CONTROL

1. Consider submitting property on Form Group?

### Other Items
1. Documentation

  - one way in one way out rule

1. Better api 

  - hub.state({ reducer, ...otherOptions }) ?

  - hub.dispatch();

  - hub.messages$

1. rename repo to RxHub

1. add a tap option for neccessary side effects

- timeout solved it

1. Clean up initil state builder method

1. More test for the initial state builder method

1. reduce boilerplate some how?

1. refactor scoped effects for action into dictionary?

### React project 

1. binding hooks and form components

1. default props? can we make the components as dumb as possible

1. Bug in react use effect on component mount, wrapper not receivign firs dispatch message