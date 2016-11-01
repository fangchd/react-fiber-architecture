
# React Fiber Architecture
https://github.com/acdlite/react-fiber-architecture

## Introduction  

The goal of React Fiber: incremental rendering

### Other key features:

- the ability to pause, abort, or reuse work as new updates come in; 
- the ability to assign priority to different types of updates; 
- and new concurrency primitives.

### Prerequisites

- [React Components, Elements, and Instances](https://facebook.github.io/react/blog/2015/12/18/react-components-elements-and-instances.html) - "Component" is often an overloaded term. A firm grasp of these terms is crucial.
- [Reconciliation](https://facebook.github.io/react/docs/reconciliation.html) - A high-level description of React's reconciliation algorithm.
- [React Basic Theoretical Concepts](https://github.com/reactjs/react-basic) - A description of the conceptual model of React without implementation burden. Some of this may not make sense on first reading. That's okay, it will make more sense with time.
- [React Design Principles](https://facebook.github.io/react/contributing/design-principles.html) - Pay special attention to the section on scheduling. It does a great job of explaining the *why* of React Fiber.

## Review
### What is reconciliation?

<dl>
  <dt>reconciliation</dt>
  <dd>The algorithm React uses to diff one tree with another to determine which parts need to be changed.</dd>

  <dt>update</dt>
  <dd>A change in the data used to render a React app. Usually the result of `setState`. Eventually results in a re-render.</dd>
</dl>

The central idea of React's API is to think of updates as if they cause the entire app to re-render.

React has optimizations which create the appearance of whole app re-rendering while maintaining great performance. The bulk of these optimizations are part of a process called **reconciliation**.

The key points are:

- Different component types are assumed to generate substantially different trees. React will not attempt to diff them, but rather replace the old tree completely.
- Differing of lists is performed using keys. Keys should be "stable, predictable, and unique."

### Reconciliation versus rendering

Fiber reimplements the reconciler. It is not principally concerned with rendering.

### Scheduling

<dl>
  <dt>scheduling</dt>
  <dd>the process of determining when work should be performed.</dd>
  
  <dt>work</dt>
  <dd>any computations that must be performed. Work is usually the result of an update (e.g. <code>setState</code>).
</dl>





