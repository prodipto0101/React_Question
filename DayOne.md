1. React Basics & JSX
✅ Question 1: What is JSX, and how is it different from HTML?
{
1. JSX is NOT HTML but looks similar.
2. JSX allows embedding JavaScript inside {}.
3. JSX uses camelCase for attributes (className instead of class).
4. JSX must be transpiled into JavaScript using Babel.
5. JSX is required for React components to define UI structure.
Why Use JSX?
    ✔ Better Readability - JSX is closer to HTML, making React components easier to understand.
    ✔ More Dynamic - Can embed JavaScript logic directly.
    ✔ Component-Based - Works seamlessly with React components.
    ✔ Performance Optimized - JSX gets converted into React.createElement() calls, which React processes efficiently.       
}

✅ Question 2: Can browsers read JSX directly? Why or why not?
{
1. No JSX(Javascript XML) need to transpile into Javascript by Using Bable
}

✅ Question 3: What are React Fragments (<React.Fragment>) and when should you use them?
{
1. React Fragments (<React.Fragment> or <>...</>) are a lightweight way to group multiple elements together without adding an extra DOM node.
In JSX, components must return a single parent element, and Fragments allow you to do this without unnecessary <div> wrappers.
✔ When returning multiple elements from a component (avoids extra <div>).
✔ When working with lists and key attributes (use <React.Fragment key={}>).
✔ When using flexbox or CSS Grid (avoids breaking layouts).
✔ When optimizing performance (reduces unnecessary DOM elements).
}

 2. React Internals & Virtual DOM
✅ Question 1: How does the React Virtual DOM work, and why is it efficient?
{
    REACT Virtual Dom Works in Three Phase.
1. Rendering Phase: When React Component is Rendered. React creats a Virtual Dom which is a JavaScript Object Representation of the actual DOM.
2. Diffin Phase: In this phase react create a New Virtual Dom if the props or states changes, while re-render happens in react.Then React the new Virtal Dom with Previous Virtual Dom.
3. Reconciliation Phase: React determines the minimum number of changes required (using an efficient diffing algorithm).Only the necessary changes are applied to the Real DOM (instead of re-rendering everything).
✔ Virtual DOM creates a lightweight copy of the Real DOM.
✔ React updates only the changed parts, not the whole DOM.
✔ Uses an efficient diffing algorithm to detect minimal updates.
✔ Reduces browser reflows & repaints, improving performance.
✔ Batch updates prevent unnecessary DOM modifications.
}

✅ Question 2: Explain the reconciliation process in React.
{
1. Rendering a New Virtual DOMWhenever state or props change, React calls the render() method of the component.
This creates a new Virtual DOM tree.
2. Diffing (Comparing Old & New Virtual DOM)
React compares the new Virtual DOM with the previous Virtual DOM.
It identifies:
Elements that changed.
Elements that were added.
Elements that were removed.
3. Patching the Real DOM (Minimal Updates)React applies the minimal number of changes to the Real DOM.This avoids unnecessary re-renders and improves performance.

}

✅ Question 3: What is React Fiber, and how is it different from the previous reconciliation algorithm?
{
React Fiber is the new reconciliation engine introduced in React 16 to improve UI rendering performance. It makes updates smoother, faster, and more efficient, especially for complex UIs.
1. Concurrent Rendering (Asynchronous Updates)
Fiber divides rendering work into small "units of work".
Instead of processing the entire component tree at once, React pauses and resumes work efficiently.
2. Task Prioritization (Scheduling)
React assigns priority levels to updates:
High Priority: User interactions (clicks, input changes).
Medium Priority: Network requests.
Low Priority: Background updates.
3. Improved Error Handling
Introduced Error Boundaries, preventing app crashes.
4. Suspense & Lazy Loading
Enables code-splitting and faster page loads.
}
✅ Question 4: How does React handle concurrent rendering?
{
    Concurrent Rendering is a React feature that allows multiple tasks to be processed without blocking the UI. Instead of handling updates synchronously (one after another), React can pause, prioritize, and resume rendering work, ensuring a smooth and responsive UI.
1. Time-Slicing (Splitting Work into Small Chunks)
React splits rendering work into small chunks and processes them in steps.If a higher-priority task (like a button click) occurs, React pauses background work to process it first.Once urgent tasks are done, React resumes paused work.

2. useTransition() (Prioritizing UI Updates)Introduced in React 18, useTransition() helps separate urgent and non-urgent updates.Urgent Updates (like typing, clicks) = processed immediately.Non-Urgent Updates (like slow calculations, data fetching) = processed in thebackground.

3. Suspense (Managing Async Data Loading)Suspense lets React pause rendering while fetching data, avoiding unnecessary loading spinners.Previously, developers used useEffect() + loading state to handle async data, which was inefficient.
}

✅ Question 5: How does React batch state updates to improve performance?
{
State batching is a performance optimization in React where multiple state updates within the same event cycle are grouped (batched) together into a single re-render instead of triggering multiple re-renders.
✅ React batches state updates to reduce unnecessary re-renders and improve performance.
✅ React 18 improves batching, even for async code!
✅ If needed, use flushSync() to force immediate updates.
}
